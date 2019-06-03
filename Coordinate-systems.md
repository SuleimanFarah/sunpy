See Thompson (2006) and Franz & Harper (2002)

| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Heliocentric Aries Ecliptic | HAE | `HeliocentricMeanEcliptic` | Use the misleadingly named `HeliocentricTrueEcliptic` if using Astropy version before v3.2 |
| Heliocentric Cartesian | HCC | `HeliocentricCartesian` | |
| Heliocentric Earth Ecliptic | HEE | none | Z=Mean ecliptic north pole, X=Sun-Earth line |
| Heliocentric Earth Equatorial | HEEQ | `HeliographicStonyhurst` | Specify the coordinate using `CartesianRepresentation` |
| Heliocentric Inertial | HCI | none | Z=Solar rotational axis, X=Solar ascending node on ecliptic; Heliocentric of Date (HCD) is the precessed version to the ecliptic of date |
| Heliocentric Radial | | ? | Equivalent to HCC with a cylindrical representation |
| Heliocentric/Heliographic Radial-Tangential-Normal | HGRTN | `HeliocentricCartesian` | The axes are permuted, with HCC X, Y, Z equivalent respectively to HGRTN Y, Z, X|
| Heliographic Carrington | HGC | `HeliographicCarrington` | |
| Heliographic Stonyhurst | HGS | `HeliographicStonyhurst` | |
| Helioprojective Cartesian | HPC | `Helioprojective` | |
| Helioprojective Radial | | ? | Is to Heliocentric Radial what HPC is to HCC |
| | | |
| Geocentric Equatorial Inertial | GEI | `PrecessedGeocentric` | For Mean GEI, not for True GEI |
| Geographic | GEO | ? | Z=True geographic north pole, X=Intersection of Greenwich meridian and geographic equator |
| Geocentric Solar Ecliptic | GSE | none | Z=Mean ecliptic north pole, X=Earth-Sun line |
| Geocentric Solar Magnetospheric | GSM | none | Z=projection of northern dipole axis on GSE YZ plane, X=Earth–Sun line |