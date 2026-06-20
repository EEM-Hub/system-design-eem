---
source: sources/wiki-Spatial_database.md
source_url: https://en.wikipedia.org/wiki/Spatial_database
---

## Spatial Databases: Storage and Querying of Geometric Data

Spatial databases extend general-purpose (typically relational) databases with spatial data types, spatial indexing, and spatial query capabilities to represent and analyze objects defined in geometric space. A geographic database (geodatabase) is a georeferenced spatial database used in GIS for storing data associated with locations on Earth. The OGC Simple Features specification (1997) and SQL/MM Spatial ISO/IEC standard define the interoperability standards for spatial database functionality.

## Key Concepts

- **Spatial database**: A database enhanced with spatial data types (geometry/feature types) and tools for querying/analyzing objects in geometric space
- **Geodatabase**: A georeferenced spatial database for storing geographic data, central to GIS workflows
- **Spatial data types**: Represent geometric primitives — points, lines, polygons; some systems support 3D objects, topological coverages, TINs, and raster data
- **Spatial reference system**: Every geographic location must be specified according to a coordinate system; spatial databases track and transform between coordinate systems
- **OGC Simple Features**: The foundational specification (1997) for representing geometric primitives and enabling interoperability across spatial systems
- **SQL/MM Spatial**: ISO/IEC standard extending Simple Features into the SQL multimedia standard
- **Five categories of spatial operations**: Measurement, Geoprocessing, Predicates, Geometry Constructors, and Observer Functions
- **Spatial index**: Multi-dimensional index structures optimized for spatial queries (linear indexing is not effective for 2D/3D data)
- **R-tree**: The typically preferred spatial indexing method; groups objects using minimum bounding rectangles (MBRs)
- **Vector vs. raster**: Most spatial databases use vector data model (points, lines, polygons); some also support raster data storage

## Commands and Syntax

**PostGIS spatial query functions (ST_ prefix convention):**
- `ST_Distance(geometry, geometry) : number` — distance between geometries
- `ST_Contains(geometry, geometry) : boolean` — containment predicate
- `ST_Intersects(geometry, geometry) : boolean` — intersection test
- `ST_Intersection(geometry, geometry) : geometry` — compute intersection geometry
- `ST_Equals`, `ST_Disjoint`, `ST_Touches`, `ST_Crosses`, `ST_Overlaps` — spatial relationship predicates
- `ST_Length(geometry) : number`, `ST_Area(geometry) : number` — measurement functions
- `ST_Centroid(geometry) : geometry` — observer function

**Spatial join example:**
```sql
SELECT * FROM cities, countries
WHERE ST_Contains(countries.shape, cities.shape)
```

**Vector overlay (intersect) example:**
```sql
SELECT ST_Intersection(veg.shape, soil.shape) int_poly, veg.*, soil.*
FROM veg, soil
WHERE ST_Intersects(veg.shape, soil.shape)
```

## Relationships

- **Relational databases**: Spatial databases are extensions of conventional RDBMS (PostgreSQL/PostGIS, Oracle Spatial, SQL Server, MySQL)
- **GIS software**: Spatial databases provide the backend storage and query engine for GIS; spatial SQL replicates operations traditionally done in GIS applications
- **NoSQL systems**: MongoDB, CouchDB, Elasticsearch offer simplified spatial capabilities
- **Graph databases**: Neo4j and AllegroGraph support spatial indexing within graph structures
- **DE-9IM**: The dimensionally extended 9-intersection model underpins spatial predicate logic
- **Spatial ETL**: Extract-transform-load processes for moving spatial data between systems
- **Spatiotemporal databases**: Extend spatial databases with time-dimension tracking
- **Big data platforms**: Apache Sedona, GeoMesa enable spatial processing on Hadoop/Spark at scale

## Exam-Relevant Points

- R-tree is the **preferred indexing method** for spatial data; it uses minimum bounding rectangles (MBRs) to group objects
- The **five spatial operation categories** defined by OGC: Measurement, Geoprocessing, Predicates, Geometry Constructors, Observer Functions
- **OGC Simple Features** (1997) is the foundational interoperability standard; **SQL/MM Spatial** extends it into ISO/IEC SQL
- PostGIS functions use the **ST_ prefix** (e.g., `ST_Contains`, `ST_Intersects`) — know the distinction between predicates (return boolean) vs. geometry constructors (return geometry) vs. measurement functions (return number)
- **Spatial queries differ from standard SQL** in two key ways: they use geometry data types and consider spatial relationships between geometries
- A spatial column definition includes a **choice of coordinate system** stored in a lookup table
- Key spatial index methods to know: R-tree, k-d tree, Quadtree, Geohash, BSP-tree
- **PostgreSQL + PostGIS** is the primary open-source OGC-compliant spatial database; MySQL had spatial limitations (MBR-only before v5.5, MyISAM-only before v5.0.16)
- Almost all current RDBMS have spatial extensions — this is no longer a niche capability
