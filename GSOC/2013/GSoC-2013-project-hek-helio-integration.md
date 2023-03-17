The Heliophysics Event Knowledgebase (HEK) is a US-based effort to collect and catalog solar and heliospheric events.  Its focus is mainly the inner heliosphere. On the other hand the [HELiophysics Integrated Observatory)[http://helio.eu] (HELIO) is a set of services which includes [Events](http://hec.helio.eu) and [Feature](http://hfc.helio.eu) catalogues (known as hec and hfc), an [Instrument Location](http://www.helio-vo.eu/services/interfaces/helio-ils_uix.php) and [Capability](http://www.helio-vo.eu/services/interfaces/helio-ics_uix.php) Service (ILS & ICS), and a [data provider access](http://www.helio-vo.eu/services/interfaces/helio-dpas_uix.php) (DPAS).  All of them can be accessed from the [main interface](http://hfe.helio.eu) and by SOAP or REST webservices. There's also a propagation model ([SHEBA](http://cagnode58.cs.tcd.ie/PropagationModelGUI/)) which helps to match events in the Sun with other locations in the heliosphere.

## Uses of HEK

Results from the HEK come with some provenance information that describe which data was used to derive the feature/event seen.  In the first case, it would be useful to connect the HEK result to the actual data using this provenance information.  In the second case, the HEK-supplied provenance information would be overwritten with choices detailed by the user.  Note that the data that is downloaded from other services should be tracked by the data database functionality (being implemented in the other GSoC 2013 project).

### Data providing services

There are two data providing services that are recommended for use with the HEK data.  The first service is the VSO.  SunPy already has a VSO module, and so data can be acquired using this service.  The second service that we would like to use is the SDO cutout service <http://www.lmsal.com/get_aia_data/> .

#### Downloading data via the VSO

HEK entries can be classed by solar features and events (F/E).  There are many different types of solar features and events, such as sunspots, flares, coronal holes, etc.  Each of these F/Es are detected by a feature recognition method (FRM).  An FRM can be an automated computation, or a detection made by a human and logged in the HEK.  Entries in the HEK have a list of F/E attributes which are listed here: <http://www.lmsal.com/hek/VOEvent_Spec.html>.

The main pieces of information of relevance to connecting the HEK to the VSO are the event start times, end times, and the Observatory (OBS) tags.  This describes when the event was observed, and what observatory saw it, using which kind of measurement (for example, which wavelength the event was seen in).

The first task is to take the HEK results, and pass that into our existing VSO data acquisition service.  This would involve parsing the HEK result and forming a VSO query to obtain the observational data.

```python
from sunpy.net import hek
H_client = hek.HEKClient()
H_result = H_client.query(....)
V_client = vso.VSOClient()
data1 = V_client.get(V_client.query(H_result[0]))
data = V_client.get(V_client.query(H_result))
```

The query client of the VSO could be extended to accept a list of HEK results.  This would make it easy to acquire the observational data from each event in the list.  Note that different events can be observed in the same observational data.  For example, let us say two solar flares occur at slightly places and times in the same set of observational image data, but the first one is of a longer duration than the second.  Each of these events will appear as a different entry in the HEK, but the image data they were seen in is the same.  Rather than downloading a longer list of files for the longer duration flare, and then a shorter list of files for the shorter duration flare, the minimum list of files that cover both flares should be used.  Or more succinctly, don't download the same file twice.

#### Downloading data via the SDO cut-out service

SDO image data is very big,  Each image is 4x by 4k pixels.  Images are taken about once per second on average.  This means the spacecraft streams down over 1 TB data/day.  Most science users only need a fraction of this data.  Obtaining that fraction is achieved through use of the SDO cut-out service.  The web client is at <http://www.lmsal.com/get_aia_data/> .  There is a Solarsoft/IDL client too.  The user specifies a time-range and a physical extent, and that portion of data is cut-out from the main archive.  The user is then sent an email when that data is ready for download from a temporary website.

HEK F/Es are typically limited in physical extent.  Returns from the HEK have a bounding box that determines the minimum sized box that encloses the F/E.  Along with the event start time, end time and Observatory information, this is sufficient information to determine a request to the cut-out service.

## Uses of HELIO

HELIO provides a large set of services, even more than the ones set above, therefore it uses can vary on what the user wants.  For now we should focus on single uses on some of the services. Notice that the webservices produces votables (AstroPy has support to that file format).  Also, it should be helpful to see what's been implemented in [solarsoft](http://www.helio-vo.eu/documents/help/ssw/helio_ssw_intro.html).

### HELIO Catalogues

The event and the feature catalogue contains a list of catalogues similar to those in HEK, but for events in all the heliosphere.

#### Events

#### Features

The feature catalogue is accessible through any of its [webservices](http://voparis-helio.obspm.fr/helio-hfc/HelioService) (I've just asked which one we should use).  This catalogue uses [PQL](http://wiki.ivoa.net/internal/IVOA/TableAccess/PQL-0.2-20090520.pdf)
and example of how to query Active Regions is:

```python
from suds import client
hfq = client.Client('http://voparis-helio.obspm.fr/hfc-hqi/HelioService?wsdl')
ARs2days = hfq.service.TimeQuery('2010-01-01T00:00:00','2010-01-02T00:00:00','VIEW_AR_HQI')
ARsLat = hfq.service.Query('2010-01-01T00:00:00','2010-01-01T02:00:00','VIEW_AR_HQI','FEAT_HG_LAT_DEG,-30/0; CODE,*smart*')
```

The first example ARs2days searches using TimeQuery and it just allows a time range from a certain table. The second example ARsLat searches with conditions.  This is following PQL syntax where the fields are separated by ';' and the values by ','.  In the example above it searching for ARs between -30 and 0 degrees in heliographic latitude and code name like 'smart'.

The interface for this should hide most of this PQL and table names away.  It should accept time objects.
Using [Taverna webservice]() we can get more info and do some sql queries

```python
hfqTav = client.Client('http://voparis-helio.obspm.fr:80/hfc-hqi/HelioTavernaService?wsdl')
print hfqTav #Shows the methods allowed from this webservice
print hfqTav.service.getTableNames() #Tells which tables we can query
ARsLatCC = hfqTav.service.SQLSelect('CC_X_PIX,CC_Y_PIX,CC','VIEW_AR_HQI',"DATE(DATE_OBS) BETWEEN DATE('2010-01-01T00:00:00') AND DATE('2010-01-02T00:00:00') AND FEAT_HG_LAT_DEG between -30 and 0 AND CODE like '%smart%'")
```

Should give the chaincode (and their starting point) for the same results than the query from above, this time using SQL syntax.  The chaincode could then be used with the chaincode routine to overplot them on a map.

Notice these examples have been based on time queries, they could work similarly without date inputs. For example if we would like to get all the active regions with certain property.

```python
ARsPropertX = hfq.service.Query('', '', 'VIEW_AR_HQI', 'FEAT_HG_LAT_DEG,-5/5; CODE,*smart*; FEAT_AREA_DEG2,/5')
ARsLatCC = hfqTav.service.SQLSelect('CC_X_PIX,CC_Y_PIX,CC','VIEW_AR_HQI',"FEAT_HG_LAT_DEG between -5 and 5 AND CODE like '%smart%' AND FEAT_AREA_DEG2 < 5")
```

### Instrument Location

ILS provides information about the location of planets and spacecraft.
