SunPy contains tools for accessing online solar and heliospheric data online.  Data can come in any of the SunPy datatypes and also as a list of HEK results.  The purpose of the local database is to track these data and make them transparently available to the user.

First question to ask is, what do we mean by 'data'?  Do we mean 'observations of the Sun and inner heliosphere taken by instrumentation', as opposed to 'data I have generated locally as a result of some computational process'.  I'm thinking here of the difference between model runs and AIA images.

Typically, a user will request a time range, and instrument, and a type of data from an online repository.  SunPy goes out to the web and downloads it.

What would the local database do?  It would take the request that was made and store it (as well as storing when the request was made), associate the request with the downloaded file, and calculate a checksum for that file, and store that.  The data should be stored locally in an easy to understand file structure so the user can go in manually and check 