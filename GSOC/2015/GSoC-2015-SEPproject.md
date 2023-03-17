# Support for analysis of Solar Energetic Particles

## Project

### Support for analysis of Solar Energetic Particles

*Suggested Mentor(s):* [David Pérez-Suárez](http://github.com/dpshelio), Timo Laitinen (University of Central Lancashire)

*Difficulty:* Beginner

*Astronomy knowledge needed:* None

*Programming skills:* Python.

#### Description

SunPy is able to read a lightcurve from different sources (GOES x-ray, Lyra, Norh,...), however these are not all.
[Solar Energetic Particles](https://en.wikipedia.org/wiki/Solar_energetic_particles) (SEPs)
are accelerated during solar eruptions up to relativistic energies.
They propagate from the Sun to the heliosphere, and arriving near Earth they pose a danger to
astronauts and spacecraft.
Thus, it is important to understand their acceleration and propagation mechanisms, so that we
can mitigate the Space Weather risk they pose.

SEPs are observed with several instruments onboard several spacecraft, such as GOES, SOHO, ACE,
and the two STEREO spacecraft.
The timing and evolution of the SEP observations are compared to observations of solar X-ray and
radio bursts, changes in solar magnetic field and EUV observations, and coronagraphs, and to the
solar wind and magnetic field properties at the observing spacecraft.
However, while many of these other observations can already be accessed with SunPy, there is as
of now no tool to analyse the SEP observations.

The SEP data is typically available as plaintext files with header information, with columns
representing energies and particle elements, while the rows represent time.
Also CDF files are used in some occasions. This project should be able to read these in as a
lightcurve object and allow to perform the basic operations used when the data is analysed.
These basic operations include:

- Visualisation as time series, including changing the time or energy resolution.
The SEP observations often suffer from low count-rates, and averaging over
energy or time is needed.
- Visualisation as energy spectrum. Combination of energies and integration over
time is important also in this case.
- Visualisation of intensity ratios of different particle species.
These ratios and their energy- and time-dependence is important for understanding
the mechanisms behind the SEP acceleration for different SEP events.

Ability of comparing the SEP observations with other light-curve type data,
such as X-ray and in-situ observations (magnetic field and solar wind propecties
near the spacecraft) would also be very useful.

## Data

### ERNE

ERNE data can be download as a 2-hour resolution Carrington rotation sets.  They are available at the srl server, and have file names of type

- <http://srl.utu.fi/erne_data/carrot/1906/cr1906p.txt>
- <http://srl.utu.fi/erne_data/carrot/1906/cr1906a.txt>

Where:

- 1906 is the Carrington rotation number (a running number of full solar rotations starting from November 9, 1853, using a rotation period of 27.2753 days)
- p is for protons, and
- a is for Helium (alpha particles).

More accurate data is also available, following the link "[Export Data](http://srl.utu.fi/erne_data/main_english.html)"

- **Level-2 EXPORT data**: The data is documented in the "[Description]()" link.

The data can also be obtained from the
[GSFC archive search tool](http://seal.nascom.nasa.gov/cgi-bin/gui_seal).
Select "ERNE" from instrument list, a date, and click
"Do search" on the bottom right.
The documentation is at the ERNE data site.

### STEREO

STEREO data can be download from:

- <http://www.srl.caltech.edu/STEREO/Public/LET_public.html>
- <http://www.srl.caltech.edu/STEREO/Public/HET_public.html>
- <http://www.srl.caltech.edu/STEREO/Public/SIT_public.html>
- <http://www2.physik.uni-kiel.de/stereo/index.php?doc=data>

### ACE

Ace data seems to be available as HDF files, at:

- <http://www.srl.caltech.edu/ACE/ASC/level2/index.html>

## Visualisation

- [This figure](http://www.aanda.org/articles/aa/full_html/2009/13/aa11386-08/img7.gif)
 ([Al-Sawad et al., 2009](http://dx.doi.org/10.1051/0004-6361/200811386))
 shows an example of a simple visualisation where in the top part
 there are some energy channels, and a He/p ratio, and magnetic field
 data (from a different instrument not available yet from SunPy).
 In the bottom part, the SEP data is combined with X-ray fluxes
 (from GOES spacecraft).

- The top panel in this
 [[other figure|GSoC-2015-SEPproject_GomezHerrero2015.png]],
 [Gomez-Herrero et al. (2015)](http://dx.doi.org/10.1088/0004-637X/799/1/55)
 shows in the top panel, lots of energies, and in the bottom,
 isotope intensity ratios.
 In some cases it would be useful to compare STEREO A/B and SOHO
 observations to compare fluxes and timings.

- [Reames (1999)](http://dx.doi.org/10.1023/A:1005105831781) shows
 [[a visualisation for the spectra|GSoC-2015-SEPproject_Reames1999.png]].
 Also a spectrum of the elemental intensity ratios would be
 very interesting.

## Operations

- **simple average**:
 If you have a energy band: 10-15 MeV, and 15-20 MeV.  "Simple average"
 for energy binning means to add them together and divide it by two.

- **Weigh channels with energy bin widths**:
 The channels are usually more or less logarithmically spaced.
 This could be improved by taking into account the
 spectrum in the weighing and calculating also the weighted energy
 point.
