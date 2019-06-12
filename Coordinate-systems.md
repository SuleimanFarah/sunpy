See Thompson (2006) and Franz & Harper (2002)

# Sun-centered coordinate systems
| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Heliocentric Aries Ecliptic | HAE (also HEC) | Astropy's `HeliocentricMeanEcliptic` | If using an Astropy version before v3.2, use the misleadingly named `HeliocentricTrueEcliptic` |
| Heliocentric Cartesian | HCC | `Heliocentric` | |
| Heliocentric Earth Ecliptic | HEE | `HeliocentricEarthEcliptic`* | Z=Mean ecliptic north pole, X=Sun-Earth line |
| Heliocentric Earth Equatorial | HEEQ (also HEQ) | `HeliographicStonyhurst` | Specify the coordinate representation using `CartesianRepresentation`, and retrieve the representation via the attribute `.cartesian` |
| Heliocentric Inertial | HCI | `HeliocentricInertial`* | Z=Solar rotational axis, X=Solar ascending node on mean ecliptic (J2000.0) |
| Heliocentric of Date | HCD | none | Z=Solar rotational axis, X=Solar ascending node on mean ecliptic of date |
| Heliocentric Radial | HCR | none | Equivalent to HCC with a cylindrical representation |
| Heliocentric/Heliographic Radial-Tangential-Normal | HGRTN | `Heliocentric` | The axes are permuted, with HCC X, Y, Z equivalent respectively to HGRTN Y, Z, X|
| Heliographic Carrington | HGC | `HeliographicCarrington` | |
| Heliographic Stonyhurst | HGS | `HeliographicStonyhurst` | |
| Helioprojective Cartesian | HPC | `Helioprojective` | |
| Helioprojective Radial | HPR | none | Is to Heliocentric Radial what HPC is to HCC |

# Earth-centered coordinate systems
| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Geocentric Equatorial Inertial (Mean) | GEI<sub>D</sub> | Astropy's `PrecessedGeocentric` | Be aware that `PrecessedGeocentric` includes aberration due to Earth motion |
| Geocentric Equatorial Inertial (True) | GEI<sub>T</sub> | none |
| Geographic | GEO | ? | Z=True geographic north pole, X=Intersection of Greenwich meridian and geographic equator |
| Geocentric Solar Ecliptic | GSE | `GeocentricSolarEcliptic`* | Z=Mean ecliptic north pole, X=Earth-Sun line |
| Geocentric Solar Magnetospheric | GSM | none | Z=projection of northern dipole axis on GSE YZ plane, X=Earth–Sun line |

\* PR is pending