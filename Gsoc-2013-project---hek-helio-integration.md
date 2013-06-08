The Heliophysics Event Knowledgebase (HEK) is a US-based effort to collect and catalog solar and heliospheric events.  Its focus is mainly the inner heliosphere. On the other hand the [HELiophysics Integrated Observatory)[http://helio.eu] (HELIO) is a set of services which includes [Events](http://hec.helio.eu) and [Feature](http://hfc.helio.eu) catalogues (known as hec and hfc), an [Instrument Location](http://www.helio-vo.eu/services/interfaces/helio-ils_uix.php) and [Capability](http://www.helio-vo.eu/services/interfaces/helio-ics_uix.php) Service (ILS & ICS), and a [data provider access](http://www.helio-vo.eu/services/interfaces/helio-dpas_uix.php) (DPAS).  All of them can be accessed from the [main interface](http://hfe.helio.eu) and by SOAP or REST webservices. There's also a propagation model ([SHEBA](http://cagnode58.cs.tcd.ie/PropagationModelGUI/)) which helps to match events in the Sun with other locations in the heliosphere.

## Uses of HEK

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
The first example ARs2days searchs using TimeQuery and it just allows a time range from a certain table. The second example ARsLat searchs with conditions.  This is following PQL syntax where the fields are separated by ';' and the values by ','.  In the example above it searching for ARs between -30 and 0 degrees in heliographic latitude and code name like 'smart'.

The interface for this should hide most of this PQL and table names away.  It should accept time objects.
Using [Taverna webservice]() we can get more info and do some sql queries
```python
hfqTav = client.Client('http://voparis-helio.obspm.fr:80/hfc-hqi/HelioTavernaService?wsdl')
print hfqTav #Shows the methods allowed from this webservice
print hfqTav.service.getTableNames() #Tells which tables we can query
ARsLatCC = hfqTav.service.SQLSelect('CC_X_PIX,CC_Y_PIX,CC','VIEW_AR_HQI',"DATE(DATE_OBS) BETWEEN DATE('2010-01-01T00:00:00') AND DATE('2010-01-02T00:00:00') AND FEAT_HG_LAT_DEG between -30 and 0 AND CODE like '%smart%'")
```
Should give the chaincode (and their starting point) for the same results than the query from above, this time using SQL sintax.  The chaincode could then be used with the chaincode routine to overplot them on a map.

Notice these examples have been based on time queries, they could work similarly without date inputs. For example if we would like to get all the active regions with certain property.
```python
ARsPropertX = hfq.service.Query('', '', 'VIEW_AR_HQI', 'FEAT_HG_LAT_DEG,-5/5; CODE,*smart*; FEAT_AREA_DEG2,/5')
ARsLatCC = hfqTav.service.SQLSelect('CC_X_PIX,CC_Y_PIX,CC','VIEW_AR_HQI',"FEAT_HG_LAT_DEG between -5 and 5 AND CODE like '%smart%' AND FEAT_AREA_DEG2 < 5")
```

### Instrument Location
ILS provides information about the location of planets and spacecraft.
