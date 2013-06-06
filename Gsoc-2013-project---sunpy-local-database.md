SunPy contains tools for accessing online solar and heliospheric data online.  Data can come in any of the SunPy datatypes and also as a list of HEK results.  The purpose of the local database is to track these data and make them transparently available to the user.

First question to ask is, what do we mean by 'data'?  Do we mean 'observations of the Sun and inner heliosphere taken by instrumentation', as opposed to 'data I have generated locally as a result of some computational process'.  I'm thinking here of the difference between model runs and AIA images.

Typically, a user will request a time range, and instrument, and a type of data from an online repository.  SunPy goes out to the web and downloads it.

What would the local database do?  Some provisional ideas.... It would take the request that was made and store it (as well as storing when the request was made), associate the request with the downloaded file, and calculate a checksum for that file, and store that.  The data should be stored locally in an easy to understand file structure so the user can go in manually and check for themselves if they want

Storing the request: perhaps the request itself could be hashed.  Then when you make the same request again, the request compares hashes and locates the data very quickly.

Storing information about the data: each data type contains information about itself.  This information is in the FITS header.  It should not be assumed that FITS keywords have the same meaning across different different data sources.

file checksum - observational data is often updated as new calibrations are made available, and so the same file name could refer to different data that have created at different times.  The user should be made aware if there is a difference in the checksum if data is redownloaded.  Both copies of the data should be retained in this case.

request time - useful for knowing when data was downloaded in relation to possible changes in the content.