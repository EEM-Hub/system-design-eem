---
source: sources/wiki-Geographic_coordinate_system.md
source_url: https://en.wikipedia.org/wiki/Geographic_coordinate_system
---

## Geographic Coordinate Systems (GCS)

A geographic coordinate system is a spherical or geodetic coordinate system for specifying positions on Earth using latitude and longitude. It is the oldest and most widely used spatial reference system. Unlike Cartesian coordinates, GCS measurements are angles on a curved surface, not distances on a plane. A complete GCS specification includes a geodetic datum (with an Earth ellipsoid), since different datums yield different coordinate values for the same physical location.

## Key Concepts

- **Latitude (φ)**: Angle north or south of the Equator (0° to 90°N/S). Lines of constant latitude are called **parallels** and trace circles parallel to the Equator.
- **Longitude (λ)**: Angle east or west of the prime meridian (0° to 180°E/W). Lines of constant longitude are called **meridians** — they are halves of great ellipses converging at the poles.
- **Prime Meridian**: The reference meridian at the Royal Observatory, Greenwich, adopted internationally in 1884. Not identical to the International Date Line.
- **Geodetic Datum**: Binds a mathematical model of Earth's shape (reference ellipsoid) to the physical Earth. Required to convert abstract lat/lon into precise real-world positions.
  - **Horizontal datum**: Measures latitude and longitude (e.g., WGS 84, NAD 83, OSGB36)
  - **Vertical datum**: Measures elevation (uses a geoid model)
- **Different datums produce different coordinates** for the same physical point — differences can be hundreds of meters (e.g., WGS 84 vs. OSGB36 differ by ~112m at Greenwich).
- **WGS 84**: The default global datum used by GPS. EPSG:4326 is the 2D ensemble with ~2m accuracy.
- **ITRF (International Terrestrial Reference Frame)**: Higher-accuracy global datum (subcentimeter) that accounts for continental drift and crustal deformation.
- **Graticule**: The visual grid of latitude and longitude lines on a map.
- **Null Island**: The 0°N, 0°E origin point, located in the Gulf of Guinea ~625 km south of Tema, Ghana.
- GCS is **not Cartesian** — measurements are angles, not planar distances.

## Commands and Syntax

**Coordinate notation formats:**
- Degrees-Minutes-Seconds (DMS): `51° 28′ 38″ N, 0° 0′ 0″ W`
- Decimal degrees: `51.4772°N, 0.0000°W`

**Length of one degree of latitude** (WGS 84, meters):
```
111132.95255 − 559.84957·cos(2φ) + 1.17514·cos(4φ) − 0.00230·cos(6φ)
```

**Length of one degree of longitude** (WGS 84, meters):
```
111412.877331·cos(φ) − 93.504117·cos(3φ) + 0.117744·cos(5φ)
```

**Simplified longitude degree length** (spherical approximation):
```
(π/180) · a · cos(β)
```
where `a = 6,378,137 m` (equatorial radius), `tan(β) = (b/a)·tan(φ)`, and `b/a = 0.99664719`.

**Reference values for longitude degree length by latitude:**

| Latitude | Degree | Minute | Second |
|----------|--------|--------|--------|
| 0° (Equator) | 111.3 km | 1.855 km | 30.92 m |
| 30° | 96.49 km | 1.61 km | 26.80 m |
| 45° | 78.85 km | 1.31 km | 21.90 m |
| 60° | 55.80 km | 0.930 km | 15.50 m |

## Relationships

- **Spatial Reference Systems**: GCS is the foundation — all map projections and projected coordinate systems (e.g., UTM) are ultimately derived from lat/lon.
- **Geodetic Datum**: A GCS without a specified datum is incomplete. Datum choice determines the reference ellipsoid and how coordinates map to physical Earth.
- **Map Projections**: Transform GCS angular coordinates onto a flat surface; each projection introduces specific distortions.
- **UTM (Universal Transverse Mercator)**: A projected coordinate system built on top of a GCS datum — a UTM coordinate on WGS 84 differs from UTM on NAD 27.
- **GNSS/GPS**: Uses WGS 84 as default datum; other datums can be selected.
- **Datum Transformations**: Converting between datums requires methods like Helmert transformation; simple translation sometimes suffices.
- **Figure of the Earth / Reference Ellipsoid / Geoid**: The mathematical models that datums use to approximate Earth's shape.

## Exam-Relevant Points

- A GCS is **not** a Cartesian coordinate system — it uses angular measurements on a curved surface.
- **A complete GCS specification requires a datum** — latitude and longitude alone are ambiguous without one.
- The same physical point has **different coordinates under different datums** — the shift can be hundreds of meters.
- **WGS 84 (EPSG:4326)** is the GPS default with ~2m accuracy; **ITRF** provides subcentimeter accuracy.
- Latitude degree length is nearly constant (~111 km); longitude degree length varies from ~111 km at the Equator to 0 km at the poles (proportional to cos φ).
- At the Equator: 1° latitude ≈ 110.6 km, 1° longitude ≈ 111.3 km. At 60° latitude, 1° longitude ≈ 55.8 km.
- **Greenwich prime meridian** was adopted in 1884 at the International Meridian Conference (22 of 25 nations agreed).
- The 180° meridian is **not identical** to the International Date Line.
- Continental drift moves points up to 10 cm/year — significant for global datums, negligible for regional ones.
- **Alternative encoding systems** (Geohash, Plus Codes, What3words, Maidenhead) are not separate coordinate systems — they are encodings of lat/lon.
- Latitude can be defined three ways: astronomical (plumb bob), geodetic (ellipsoid normal), or geocentric (center of Earth).
- The Equator is the **fundamental plane** of all geographic coordinate systems.
