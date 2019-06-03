See Thompson (2006) and Franz & Harper (2002)

# Sun-centered coordinate systems
| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Heliocentric Aries Ecliptic | HAE (also HEC) | Astropy's `HeliocentricMeanEcliptic` | If using an Astropy version before v3.2, use the misleadingly named `HeliocentricTrueEcliptic` |
| Heliocentric Cartesian | HCC | `HeliocentricCartesian` | |
| Heliocentric Earth Ecliptic | HEE | none | Z=Mean ecliptic north pole, X=Sun-Earth line |
| Heliocentric Earth Equatorial | HEEQ (also HEQ) | `HeliographicStonyhurst` | Specify the coordinate using `CartesianRepresentation` |
| Heliocentric Inertial | HCI | none | Z=Solar rotational axis, X=Solar ascending node on ecliptic; Heliocentric of Date (HCD) is the precessed version to the ecliptic of date; similar to the "de-tilted HCRS" frame that is used for internal calculations, but that one is not dynamical |
| Heliocentric Radial | HCR | none | Equivalent to HCC with a cylindrical representation |
| Heliocentric/Heliographic Radial-Tangential-Normal | HGRTN | `HeliocentricCartesian` | The axes are permuted, with HCC X, Y, Z equivalent respectively to HGRTN Y, Z, X|
| Heliographic Carrington | HGC | `HeliographicCarrington` | |
| Heliographic Stonyhurst | HGS | `HeliographicStonyhurst` | |
| Helioprojective Cartesian | HPC | `Helioprojective` | |
| Helioprojective Radial | HPR | none | Is to Heliocentric Radial what HPC is to HCC |

# Earth-centered coordinate systems
| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Geocentric Equatorial Inertial | GEI | Astropy's `PrecessedGeocentric` | For Mean GEI, not for True GEI |
| Geographic | GEO | ? | Z=True geographic north pole, X=Intersection of Greenwich meridian and geographic equator |
| Geocentric Solar Ecliptic | GSE | none | Z=Mean ecliptic north pole, X=Earth-Sun line |
| Geocentric Solar Magnetospheric | GSM | none | Z=projection of northern dipole axis on GSE YZ plane, X=Earth–Sun line |