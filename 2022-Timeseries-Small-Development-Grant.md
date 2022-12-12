# sunpy.timeseries small development grant
## Proposal Title
Scoping the future of timeseries data in sunpy.

## Two Sentence Summary of Proposal
The data storage container for timeseries data in sunpy does not support all solar physics datasets. We propose to scope out user requirements for a new timeseries storage container, and use these to identify a new internal data container.

## Description of Proposal

Data that varies as a function of time is widely used for solar physics. Currently this is supported in sunpy via the TimeSeries data container. This uses pandas.DataFrame as a base internal data container, with solar physics specific functionality added on top. While pandas.DataFrame has the advantages of being a mature and generic container that is widely used across the scientific Python ecosystem, it is not built with solar physics in mind. This has lead to several issues when handling solar physics datasets:

1. Some data contain timestamps with leap seconds, which pandas has no support for. Users cannot currently load any data that contains leap seconds.
2. sunpy has to maintain a custom compatibility layer and API in order to store physical units (e.g. meters, seconds) associated with the data.
3. Some datasets also vary along additional dimensions to time, such as physical space. pandas is not designed to store multidimensional-data of this type.
4. Data often contains masked values, and pandas has no support for masking generic data types.

Because of these issues, the SunPy project has decided the internal data container for timeseries data needs to be replaced. Because sunpy is a mature software library that prioritises not breaking user code without warning, making this change will be a complex operation, as evidenced by a previous attempt to do this (https://github.com/sunpy/sunpy/pull/5834). We therefore want to carefully choose and implement an internal data container once and for the long term, taking into account usability, maintainability, and integration opportunities with the wider scientific Python ecosystem.

We are applying for a small development grant to scope the requirements for and choose an appropriate storage container for timeseries data in sunpy.
Accomplishing this requires the following steps

1. Gathering user requirements for timeseries data
2. Translating these into requirements for an internal data container.
3. Evaluating possible containers against these requirements. Containers we are currently considering are:
- pandas.DataFrame
- astropy.timeseries.TimeSeries
- ndcube.NDCube
- xarray.DataArray
4. Recommending a container to implement, discussing with the community, and arriving at a consensus community choice.

In addition to this scoping work, the path to implementing the container will be prepared by increasing the test coverage of sunpy.timeseries from 93% to 100%. This will ensure when making the change of container in future we do not break any user workflows without first warning them of upcoming changes.

## Please explain the benefit of this proposal including:
No more than 400 words (2,500 characters max)
### Impact to the project
Spending the time to do a proper scoping job will ensure we only have to make a complicated change to the code base once and for the long term. Doing a proper scoping job before implementation will also ensure no time is wasted on attempts to implement a new data container without full consideration of the best option.

### Impact to the scientific ecosystem
All options being considered are part of the wider scientific Python ecosystem, and whichever is chosen will benefit from upstream contributions from the SunPy developer community. Ensuring our chosen data container is interoperable with other packages (including other Matplotlib, scipy, astropy, pysat, pandas, xarray, dask) will reduce duplication of developer effort on both SunPy and other packages parts.

### Impact to the community
Being able to support a wide range of solar physics timeseries datasets will ensure sunpy continues to serve its scientific community during and beyond the next decade. This is particularly important for supporting data analysis with the new generation solar physics missions (e.g. ESA’s Solar Orbiter, NASA’s Parker Solar Probe, ISRO’s Aditya-L1).

# Outcome
Funded by NUMFocus. Feedback on proposal:


"Good proposal and description of the benefit to the community, especially the upstream projects. The detail and breakdown in the budget is also appreciated. The timeline seems unnecessarily stretched out, and with only 10 hours scheduled per month, the rate of pay seems quite high; how much time will the maintainer spend getting back up to speed on the progress, vs actually making progress with only 1.25 days per month?"
