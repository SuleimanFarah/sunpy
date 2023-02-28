## Background
SunPy contains tools for accessing online solar and heliospheric data online.  Data can come in any of the SunPy datatypes and also as a list of HEK results.  The purpose of the local database is to track these data and make them transparently available to the user. Another advantage is that the system would know what data is available and could intercept new data requests if the data has already been downloaded saving bandwidth.

First question to ask is, what do we mean by 'data'?  Do we mean 'observations of the Sun and inner heliosphere taken by instrumentation', as opposed to 'data I have generated locally as a result of some computational process'.  I'm thinking here of the difference between model runs and AIA images.

Typically, a user will request a time range, and instrument, and a type of data from an online repository.  SunPy goes out to the web and downloads it.

What would the local database do?  Some provisional ideas.... It would take the request that was made and store it (as well as storing when the request was made), associate the request with the downloaded file, and calculate a checksum for that file, and store that.  The data should be stored locally in an easy to understand file structure so the user can go in manually and check for themselves if they want. The metadata should be stored in a fast and efficient database structure. An intuitive public interface to this database should also be made available to the user.

## Database Definition
Each file would have an associated entry in database table. The fields are populated using information from the request itself as well as data contained within the downloaded file. Most files which users will be downloading as FITS files which have a wealth of metadata in their headers. It should not be assumed that FITS keywords have the same meaning across different different data sources. The map object can already translate to a set of metadata for different instruments. It might be useful to keep all header attributes as meta-data, if the user desires to query for them (with a one-to-many to key, value entries).

Summary List Database fields
* **hash of request** - when you make the same request again, the request compares hashes and locates the data very quickly.
* **hash of downloaded file** - observational data is often updated as new calibrations are made available, and so the same file name could refer to different data that have created at different times.  The user should be made aware if there is a difference in the checksum if data is redownloaded.  Both copies of the data should be retained in this case.
* **file name**
* **date downloaded or request time** - useful for knowing when data was downloaded in relation to possible changes in the content.
* **source URL**
* **instrument** (e.g. AIA)
* **observatory** (e.g. SDO)
* **wavelength**
* **time of observation**
* **data level** (e.g. 1.0)
* **small thumbnail?** this would be useful for large files but maybe we make this optional. thumbnail could also be saved in a file elsewhere and not in the database itself. alternatively as a blob. evaluate both options.
* **associated hek event tag** (this would allow multiple observations to be linked to a single event)
* **camera position or position of observer**
* **file size**?
* **user comment**
* **starred** boolean field. convenience method to get all starred entries.
* **user tags**?

## Questions to answer
* Should a user be able to query the database directly or only through a data search?
* If so, what should be the result of a query? Define the query response object.
* What field values are optional? What are required?

## Usage Case Examples
