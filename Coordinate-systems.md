# Coordinate Systems

See Thompson (2006) and Franz & Harper (2002)

## Sun-centered coordinate systems

| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Heliocentric Aries Ecliptic (Mean J2000.0 or Date) | HAE (also HEC) | Astropy's `HeliocentricMeanEcliptic` | If using an Astropy version before v3.2, use the misleadingly named `HeliocentricTrueEcliptic` |
| Heliocentric Cartesian | HCC | `Heliocentric` | Z=Sun-observer line, YZ-plane contains solar rotation axis |
| Heliocentric Earth Ecliptic | HEE | `HeliocentricEarthEcliptic` | X=Sun-Earth line, XZ-plane contains the mean ecliptic north pole |
| Heliocentric Earth Equatorial | HEEQ (also HEQ) | `HeliographicStonyhurst` | Specify the coordinate representation using `CartesianRepresentation`, and retrieve the representation via the attribute `.cartesian` |
| Heliocentric Inertial | HCI | `HeliocentricInertial` | Z=solar rotational axis, X=solar ascending node on mean ecliptic (J2000.0) |
| Heliocentric of Date | HCD | none | Z=solar rotational axis, X=solar ascending node on mean ecliptic of date |
| Heliocentric Radial | HCR | ~`Heliocentric` | Use a cylindrical representation, *but* with a 90-degree offset in psi because `Heliocentric` in cylindrical measures counter-clockwise from the west limb rather than solar north |
| Heliocentric/Heliographic Radial-Tangential-Normal | HGRTN | ~`Heliocentric` | The axes are permuted, with HCC X, Y, Z equivalent respectively to HGRTN Y, Z, X|
| Heliographic Carrington | HGC | `HeliographicCarrington` | |
| Heliographic Stonyhurst | HGS | `HeliographicStonyhurst` | |
| Helioprojective Cartesian | HPC | `Helioprojective` | |
| Helioprojective Radial | HPR | none | Is to Heliocentric Radial what HPC is to HCC |

## Earth-centered coordinate systems

| Coordinate system | Abbreviation | SunPy/Astropy equivalent | Notes |
| --- | --- | --- | --- |
| Geocentric Earth Equatorial (Mean J2000.0 or Date) | GEI<sub>J2000</sub> or GEI<sub>D</sub> | `GeocentricEarthEquatorial` | Astropy's `PrecessedGeocentric` is similar, but includes aberration due to Earth motion |
| Geocentric Earth Equatorial (True) | GEI<sub>T</sub> | none |
| Geographic | GEO | Astropy's `ITRS` | Z=true geographic north pole, X=intersection of Greenwich meridian and geographic equator |
| Geocentric Solar Ecliptic | GSE | `GeocentricSolarEcliptic` | X=Earth-Sun line, XZ-plane contains the mean ecliptic north pole |
| Geocentric Solar Magnetospheric | GSM | none | Z=projection of northern dipole axis on GSE YZ plane, X=Earth–Sun line |
