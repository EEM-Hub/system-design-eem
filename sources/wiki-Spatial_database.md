---
source: https://en.wikipedia.org/wiki/Spatial_database
fetched: 2026-06-19
---

Database of data representing objects in geometric space 

A **spatial database** is a general-purpose [database](./Database) (usually a [relational database](./Relational_database)) that has been enhanced to include [spatial data](./Spatial_data) that represents objects defined in a [geometric space](./Space), along with tools for [querying](./Information_retrieval) and analyzing such data.  

 

Most spatial databases allow the representation of simple geometric objects such as [points](./Point_(geometry)), [lines](./Line_(geometry)) and [polygons](./Polygon). Some spatial databases handle more complex structures such as [3D objects](./Solid_geometry), [topological coverages](./Coverage_data), linear networks, and [triangulated irregular networks](./Triangulated_irregular_network) (TINs). While typical databases have developed to manage various numeric and character [types of data](./Data_type), such databases require additional functionality to process spatial data types efficiently, and developers have often added *geometry* or *feature* data types. 

 

**Geographic database** (or **geodatabase**) is a [georeferenced](./Georeferenced) spatial database, used for storing and manipulating [geographic data](./Geographic_data) (or geodata, i.e., data associated with a location on Earth),[[a]](./Spatial_database#cite_note-1) especially in [geographic information systems](./Geographic_information_systems) (GIS). Almost all current relational and object-relational database management systems now have spatial extensions, and some GIS software vendors have developed their own spatial extensions to database management systems.

 

The [Open Geospatial Consortium](./Open_Geospatial_Consortium) (OGC) developed the *[Simple Features](./Simple_Features)* specification (first released in 1997)[[1]](./Spatial_database#cite_note-2) and sets standards for adding spatial functionality to database systems.[[2]](./Spatial_database#cite_note-3) The *SQL/MM Spatial* ISO/IEC standard is a part of the structured query language and multimedia standard extending the Simple Features.[[3]](./Spatial_database#cite_note-Kresse2012-4)

 

## Characteristics

 

The core functionality added by a spatial extension to a database is one or more *spatial datatypes*, which allow for the storage of spatial data as attribute values in a table.[[4]](./Spatial_database#cite_note-GISTBOK-5) Most commonly, a single spatial value would be a [geometric primitive](./Geometric_primitive) (point, line, polygon, etc.) based on the [vector data model](./Data_model_(GIS)#Vector_data_model). The datatypes in most spatial databases are based on the OGC [Simple Features](./Simple_Features) specification for representing geometric primitives. Some spatial databases also support the storage of [raster data](./Raster_graphics). Because all geographic locations must be specified according to a [spatial reference system](./Spatial_reference_system), spatial databases must also allow for the tracking and transformation of coordinate systems. In many systems, when a spatial column is defined in a table, it also includes a choice of coordinate system, chosen from a list of available systems that is stored in a lookup table.

 

The second major functionality extension in a spatial database is the addition of spatial capabilities to the query language (e.g., [SQL](./SQL)); these give the spatial database the same [ query, analysis, and manipulation operations](./Spatial_analysis) that are available in traditional GIS software. In most relational database management systems, this functionality is implemented as a set of new functions that can be used in SQL SELECT statements. Several types of operations are specified by the [Open Geospatial Consortium](./Open_Geospatial_Consortium) standard:

 
- Measurement: Computes line length, polygon area, the distance between geometries, etc.
- Geoprocessing: Modify existing features to create new ones, for example by creating a buffer around them, intersecting features, etc.
- Predicates: Allows true/false queries about spatial relationships between geometries.  Examples include "do two polygons overlap?" or 'is there a residence located within a mile of the area we are planning to build the landfill?' (see [DE-9IM](./DE-9IM))
- Geometry Constructors: Creates new geometries, usually by specifying the vertices (points or nodes) which define the shape.
- Observer Functions: Queries that return specific information about a feature, such as the location of the center of a circle.

 

Some databases support only simplified or modified sets of these operations, especially in cases of [NoSQL](./NoSQL) systems like [MongoDB](./MongoDB) and [CouchDB](./CouchDB).

 

## Spatial index

 

A **spatial index** is used by a spatial database to optimize [spatial queries](./Spatial_query), implementing spatial access methods.  Database systems use indices to quickly look up values by sorting data values in a linear (e.g. alphabetical) order; however, this way of indexing data is not optimal for [spatial queries](./Spatial_query) in two- or three-dimensional space. Instead, spatial databases use a *spatial* index designed specifically for multi-dimensional ordering.[[5]](./Spatial_database#cite_note-GISTBOK_indexing-6) Common spatial index methods include:

 
- [Binary space partitioning](./Binary_space_partitioning) (BSP-Tree): Subdividing space by hyperplanes.
- [Bounding volume hierarchy](./Bounding_volume_hierarchy) (BVH)
- [Geohash](./Geohash)
- [Grid (spatial index)](./Grid_(spatial_index))
- [HHCode](./HHCode)
- [Hilbert R-tree](./Hilbert_R-tree)
- [*k*-d tree](./K-d_tree)
- [m-tree](./M-tree) – an m-tree index can be used for the efficient resolution of similarity queries on complex objects as compared using an arbitrary metric.
- [Octree](./Octree)
- [PH-tree](./PH-tree)
- [Quadtree](./Quadtree)
- [R-tree](./R-tree): Typically the preferred method for indexing spatial data.[[6]](./Spatial_database#cite_note-7) Objects (shapes, lines and points) are grouped using the [minimum bounding rectangle](./Minimum_bounding_rectangle) (MBR). Objects are added to an MBR within the index that will lead to the smallest increase in its size.
- [R+ tree](./R+_tree)
- [R* tree](./R*_tree)
- [UB-tree](./UB-tree)
- [X-tree](./X-tree)
- [Z-order (curve)](./Z-order_(curve))

 

## Spatial query

 

A **spatial query** is a special type of [database query](./Database_query) supported by spatial databases, including geodatabases. The queries differ from non-spatial [SQL](./SQL) queries in several important ways. Two of the most important are that they allow for the use of geometry data types such as points, lines and polygons and that these queries consider the spatial relationship between these geometries.

 

The function names for queries differ across geodatabases. The following are a few of the functions built into [PostGIS](./PostGIS), a free geodatabase which is a PostgreSQL extension (the term 'geometry' refers to a point, line, box or other two or three dimensional shape):[[7]](./Spatial_database#cite_note-8)

 

Function prototype: *functionName (parameter(s)) : return type *

 
- `ST_Distance(geometry, geometry) : number`
- `ST_Equals(geometry, geometry) : boolean`
- `ST_Disjoint(geometry, geometry) : boolean`
- `ST_Intersects(geometry, geometry) : boolean`
- `ST_Touches(geometry, geometry) : boolean`
- `ST_Crosses(geometry, geometry) : boolean`
- `ST_Overlaps(geometry, geometry) : boolean`
- `ST_Contains(geometry, geometry) : boolean`
- `ST_Length(geometry) : number`
- `ST_Area(geometry) : number`
- `ST_Centroid(geometry) : geometry`
- `ST_Intersection(geometry, geometry) : geometry`

 

Thus, a [spatial join](./Spatial_join) between a points layer of cities and a polygon layer of countries could be performed in a spatially-extended SQL statement as:

 
```
SELECT * FROM cities, countries WHERE ST_Contains(countries.shape, cities.shape)

```
 

The Intersect [vector overlay](./Vector_overlay) operation (a core element of GIS software) could be replicated as:

 
```
SELECT ST_Intersection(veg.shape, soil.shape) int_poly, veg.*, soil.* FROM veg, soil where ST_Intersects(veg.shape, soil.shape)

```
 

## Spatial database management systems

 Main category: [Spatial database management systems](./Category:Spatial_database_management_systems) Main category: [Geographical databases](./Category:Geographical_databases) 

### List

 Entries in this list should be "notable" and already have a sourced Wikipedia article (see WP:GNG). 
- [AllegroGraph](./AllegroGraph) – a [graph database](./Graph_database) which provides a mechanism for efficient storage and retrieval of two-dimensional geospatial coordinates for [Resource Description Framework](./Resource_Description_Framework) data.[*[citation needed](./Wikipedia:Citation_needed)*] It includes an extension syntax for [SPARQL](./SPARQL) queries.
- [ArangoDB](./ArangoDB) - a multi-model database which provides geoindexing capability.
- [Apache Drill](./Apache_Drill) - A MPP SQL query engine for querying large datasets.  Drill supports spatial data types and functions [[8]](./Spatial_database#cite_note-9) similar to PostgreSQL.
- [Apache Sedona](./Apache_Sedona) supports scalable geospatial processing and spatial SQL on top of Apache Spark for databases and big data analytics systems.[[9]](./Spatial_database#cite_note-10)
- Esri [Geodatabase](./Geodatabase_(Esri)) (Enterprise, Mobile) - a proprietary spatial database structure and logical model that can be implemented on several relational databases, both commercial (Oracle, MS SQL Server, Db2) and open source (PostgreSQL, SQLite)
- [Caliper](./Caliper_Corporation) extends the Raima Data Manager with spatial datatypes, functions, and utilities.
- [CouchDB](./CouchDB) a document-based database system that can be spatially enabled by a plugin called Geocouch
- [Elasticsearch](./Elasticsearch) is a document-based database system that supports two types of geo data: geo_point fields which support lat/lon pairs, and geo_shape fields, which support points, lines, circles, polygons, multi-polygons, etc.[[10]](./Spatial_database#cite_note-11)
- [GeoMesa](./GeoMesa) is a cloud-based spatio-temporal database built on top of [Apache Accumulo](./Apache_Accumulo) and [Apache Hadoop](./Apache_Hadoop) (also supports [Apache HBase](./Apache_HBase), [Google](./Google) [Bigtable](./Bigtable), [Apache Cassandra](./Apache_Cassandra), and [Apache Kafka](./Apache_Kafka)). GeoMesa supports full OGC [Simple Features](./Simple_Features) and a GeoServer plugin.
- [H2](./H2_(DBMS)) supports geometry types[[11]](./Spatial_database#cite_note-12) and spatial indices[[12]](./Spatial_database#cite_note-13) as of version 1.3.173 (2013-07-28). An extension called H2GIS available on Maven Central gives full OGC [Simple Features](./Simple_Features) support.
- Any edition of [IBM Db2](./IBM_Db2) can be spatially-enabled to implement the OpenGIS spatial functionality with SQL spatial types and functions.
- [IBM Informix](./IBM_Informix) Geodetic and Spatial datablade extensions auto-install on use and expand Informix's datatypes to include multiple standard coordinate systems and support for RTree indexes. Geodetic and Spatial data can also be incorporated with Informix's Timeseries data support for tracking objects in motion over time.
- [Linter SQL Server](./Linter_SQL_RDBMS) supports spatial types and spatial functions according to the OpenGIS specifications.
- [Microsoft SQL Server](./Microsoft_SQL_Server) has support for spatial types since version 2008
- [MonetDB/GIS](./MonetDB#GIS) extension for [MonetDB](./MonetDB) adds OGS Simple Features to the relational [column-store](./Column-oriented_database) database.[[13]](./Spatial_database#cite_note-gis-14)
- [MySQL](./MySQL) DBMS implements the datatype *geometry*, plus some spatial functions implemented according to the OpenGIS specifications.[[14]](./Spatial_database#cite_note-15) However, in MySQL version 5.5 and earlier, functions that test spatial relationships are limited to working with minimum bounding rectangles rather than the actual geometries. MySQL versions earlier than 5.0.16 only supported spatial data in MyISAM tables. As of MySQL 5.0.16, InnoDB, NDB, BDB, and ARCHIVE also support spatial features.
- [Neo4j](./Neo4j) – a [graph database](./Graph_database) that can build 1D and 2D indexes as [B-tree](./B-tree), [Quadtree](./Quadtree) and [Hilbert curve](./Hilbert_curve) directly in the [graph](./Graph_(discrete_mathematics))
- [OpenLink Virtuoso](./Virtuoso_Universal_Server) has supported SQL/MM since version 6.01.3126,[[15]](./Spatial_database#cite_note-16) with significant enhancements including [GeoSPARQL](./GeoSPARQL) in Open Source Edition 7.2.6, and in Enterprise Edition 8.2.0[[16]](./Spatial_database#cite_note-17)
- [Oracle Spatial](./Oracle_Spatial)
- [PostgreSQL](./PostgreSQL) DBMS (database management system) uses the extension [PostGIS](./PostGIS) to implement OGC-compliant [[17]](./Spatial_database#cite_note-18) spatial functionality, including standardized datatype *geometry* and corresponding functions.
- [Redis](./Redis) with the Geo API.[[18]](./Spatial_database#cite_note-19)
- [RethinkDB](./RethinkDB) supports geospatial indexes in 2D.
- [SAP HANA](./SAP_HANA) supports geospatial with SPS08.[[19]](./Spatial_database#cite_note-20)
- [Smallworld](./Smallworld) [VMDS](./VMDS), the native GE [Smallworld](./Smallworld) GIS database
- [SpaceTime](https://www.mireo.com/spacetime) is a commercial spatiotemporal database built on top of the proprietary multidimensional index similar to the [*k*-d tree](./K-d_tree) family, but created using the bottom-up approach and adapted to particular space-time distribution of data.
- [Spatial Query Server](./Spatial_Query_Server) from [Boeing](./Boeing) spatially enables Sybase ASE.
- [SpatiaLite](./SpatiaLite) extends [Sqlite](./Sqlite) with spatial datatypes, functions, and utilities.
- [Tarantool](./Tarantool) supports geospatial queries with RTREE index.[[20]](./Spatial_database#cite_note-21)
- [Teradata Geospatial](./Teradata_Geospatial) includes 2D spatial functionality (OGC-compliant) in its data warehouse system.
- [Vertica Place](./Vertica), the geo-spatial extension for [HP Vertica](./HP_Information_Management_Software#HP_Vertica), adds OGC-compliant spatial features to the relational [column-store](./Column-oriented_database) database.[[21]](./Spatial_database#cite_note-verticaplace-22)
- Wherobots is a cloud-based geospatial analytics database platform built on top of [Apache Sedona](./Apache_Sedona).[[22]](./Spatial_database#cite_note-23) Supports spatial processing and data for mobility, agritech, insurance, energy, telecom, retail, logistics industries.[[23]](./Spatial_database#cite_note-24)

 

### Table of free systems especially for spatial data processing

 Entries in this table should be "notable" and already have a sourced Wikipedia article (see WP:GNG).  
| DBS | License | Distributed | Spatial objects | Spatial functions | PostgreSQLinterface | UMNMapServerinterface | Documentation | Modifiable | HDFS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Apache Drill | Apache License 2.0 | Yes | Yes | Yes -Drill Geospatial Functions Documentation | Yes | No | OfficialDocumentation | ANSISQL | Yes |
| ArangoDB | Apache License 2.0 | Yes | Yes | Yes -capabilities overviewquery language functions | No | No | officialdocumentation | AQL | No |
| GeoMesa | Apache License2.0 | Yes | Yes (Simple Features) | Yes (JTS) | No (manufacturable withGeoTools) | No | parts of the functions, a few examples | withSimple Feature AccessinJava Virtual MachineandApache Sparkare all kinds of tasks solvable | Yes |
| H2(H2GIS) | LGPL3 (since v1.3),GPL3 before | No | Yes (custom, no raster) | Simple Feature Accessand custom functions for H2Network | Yes | No | Yes (homepage) | SQL | No |
| Ingres | GPLor proprietary | Yes (if extension is installed) | Yes (custom, no raster) | Geometry Engine, Open Source[24] | No | with MapScript | just briefly | with C and OME | No |
| Neo4J-spatial[25] | GNU affero general public license | No | Yes (Simple Features) | Yes (contain, cover, covered by, cross, disjoint, intersect, intersect window, overlap, touch, within and within distance) | No | No | just briefly | fork ofJTS | No |
| PostgreSQLwithPostGIS | GNU General Public License | No | Yes (Simple Featuresand raster) | Yes (Simple Feature Accessand raster functions) | Yes | Yes | detailed | SQL, in connection withR | No |
| Postgres-XLwithPostGIS | Mozilla public license and GNU general public license | Yes | Yes (Simple Featuresand raster) | Yes (Simple Feature Accessand raster functions) | Yes | Yes | PostGIS: yes, Postgres-XL: briefly | SQL, in connection withRorTclorPython | No |
| Rasdaman | serverGPL, clientLGPL, enterprise proprietary | Yes | just raster | raster manipulation with rasql | Yes | withWeb Coverage ServiceorWeb Processing Service | detailed wiki | own defined function in enterprise edition | No |
| RethinkDB | AGPL | Yes | Yes | distancegetIntersectinggetNearestincludesintersects | No | No | official documentation[26] | forking | No |

 

## See also

 
- [Geographic information system](./Geographic_information_system) (GIS)
- [GeoSPARQL](./GeoSPARQL)
- [Glacio-geological databases](./Glacio-geological_databases)
- [Location intelligence](./Location_intelligence)
- [Multimedia database](./Multimedia_database)
- [Nearest neighbor search](./Nearest_neighbor_search)
- [Object-based spatial database](./Object-based_spatial_database)
- [Simple Features](./Simple_Features)
- [Spatial analysis](./Spatial_analysis)
- [Spatial ETL](./Spatial_ETL)
- [Spatiotemporal database](./Spatiotemporal_database)

 

## Notes

  
1. [↑](./Spatial_database#cite_ref-1) The term "geodatabase" may also refer specifically to a set of proprietary spatial database formats, [Geodatabase (Esri)](./Geodatabase_(Esri)).

 

## References

  
1. [↑](./Spatial_database#cite_ref-2) McKee, Lance (2016). ["OGC History (detailed)"](http://www.opengeospatial.org/ogc/historylong). OGC. Retrieved 2016-07-12. [...] 1997 [...] OGC released the OpenGIS Simple Features Specification, which specifies the interface that enables diverse systems to communicate in terms of 'simple features' which are based on 2D geometry. The supported geometry types include points, lines, linestrings, curves, and polygons. Each geometric object is associated with a Spatial Reference System, which describes the coordinate space in which the geometric object is defined.
2. [↑](./Spatial_database#cite_ref-3)  [OGC Homepage](http://www.opengeospatial.org)
3. [↑](./Spatial_database#cite_ref-Kresse2012_4-0) Kresse, Wolfgang; Danko, David M., eds. (2010). [*Springer handbook of geographic information*](https://archive.org/details/springerhandbook00kres) (1. ed.). Berlin: Springer. pp. [82](https://archive.org/details/springerhandbook00kres/page/n109)–83. [ISBN](./ISBN_(identifier)) [9783540726807](./Special:BookSources/9783540726807). 
4. [↑](./Spatial_database#cite_ref-GISTBOK_5-0) Yue, P.; Tan, Z. ["DM-03 - Relational DBMS and their Spatial Extensions"](https://gistbok.ucgis.org/bok-topics/relational-dbms-and-their-spatial-extensions). *GIS&T Body of Knowledge*. UCGIS. Retrieved 5 January 2023.
5. [↑](./Spatial_database#cite_ref-GISTBOK_indexing_6-0) Zhang, X.; Du, Z. ["DM-66 Spatial Indexing"](http://gistbok.ucgis.org/bok-topics/spatial-indexing). *GIS&T Body of Knowledge*. UCGIS. Retrieved 5 January 2023.
6. [↑](./Spatial_database#cite_ref-7) Güting, Ralf Hartmut; Schneider, Markus (2005). *Moving Objects Databases*. Morgan Kaufmann. p. 262. [ISBN](./ISBN_(identifier)) [9780120887996](./Special:BookSources/9780120887996).
7. [↑](./Spatial_database#cite_ref-8) ["PostGIS Function Reference"](https://postgis.net/docs/reference.html). *PostGIS Manual*. OSGeo. Retrieved 4 January 2023.
8. [↑](./Spatial_database#cite_ref-9) [](https://drill.apache.org/docs/gis-functions/) Drill Geospatial Function Documentation
9. [↑](./Spatial_database#cite_ref-10) Forrest, Matt (2025-05-13). ["How to Run Scalable Geospatial Analysis with Apache Sedona – Right From Your Laptop - Matt Forrest"](https://forrest.nyc/how-to-run-scalable-geospatial-analysis-with-apache-sedona-right-from-your-laptop/). Retrieved 2025-10-10.
10. [↑](./Spatial_database#cite_ref-11) ["Geo queries | Elasticsearch Guide [7.15] | Elastic"](https://www.elastic.co/guide/en/elasticsearch/reference/current/geo-queries.html).
11. [↑](./Spatial_database#cite_ref-12) [H2 geometry type documentation](http://www.h2database.com/html/datatypes.html#geometry_type)
12. [↑](./Spatial_database#cite_ref-13) [H2 create spatial index documentation](http://www.h2database.com/html/grammar.html#create_index)
13. [↑](./Spatial_database#cite_ref-gis_14-0) ["GeoSpatial – MonetDB"](http://www.monetdb.org/Documentation/Extensions/GIS). 4 March 2014.
14. [↑](./Spatial_database#cite_ref-15) ["MySQL 5.5 Reference Manual - 12.17.1. Introduction to MySQL Spatial Support"](https://web.archive.org/web/20130430004440/http://dev.mysql.com/doc/refman/5.5/en/gis-introduction.html). Archived from [the original](http://dev.mysql.com/doc/refman/5.5/en/gis-introduction.html) on 2013-04-30. Retrieved 2013-05-01.
15. [↑](./Spatial_database#cite_ref-16) OpenLink Software. ["9.34. Geometry Data Types and Spatial Index Support"](http://docs.openlinksw.com/virtuoso/sqlrefgeospatial/). Retrieved October 24, 2018.
16. [↑](./Spatial_database#cite_ref-17) OpenLink Software (2018-10-23). ["New Releases of Virtuoso Enterprise and Open Source Editions"](https://medium.com/virtuoso-blog/new-releases-of-virtuoso-enterprise-and-open-source-editions-a3b39d2a076). Retrieved October 24, 2018.
17. [↑](./Spatial_database#cite_ref-18) ["OGC Certified PostGIS"](https://www.ogc.org/resource/products/details/?pid=1591).
18. [↑](./Spatial_database#cite_ref-19) ["Command reference – Redis"](http://redis.io/commands/#geo).
19. [↑](./Spatial_database#cite_ref-20) ["SAP Help Portal"](http://help.sap.com/hana/sap_hana_spatial_reference_en.pdf) (PDF).
20. [↑](./Spatial_database#cite_ref-21) ["RTREE"](https://web.archive.org/web/20141213221030/http://tarantool.org/doc/user_guide/RTREE.html). *tarantool.org*. Archived from [the original](http://tarantool.org/doc/user_guide/RTREE.html#in-memory) on 2014-12-13. 
21. [↑](./Spatial_database#cite_ref-verticaplace_22-0) ["HP Vertica Place"](https://saas.hpe.com/marketplace/haven/hp-vertica-place-720). 2 December 2015.
22. [↑](./Spatial_database#cite_ref-23) Alamalhodaei, Aria (2023-06-13). ["Wherobots is building a data platform to treat spatial data as a 'first-class citizen'"](https://techcrunch.com/2023/06/13/wherobots-is-building-a-data-platform-to-treat-spatial-data-as-a-first-class-citizen/). *TechCrunch*. Retrieved 2025-09-24.
23. [↑](./Spatial_database#cite_ref-24) Rubinstein, David (2025-10-30). ["Gaining AI insights from spatial data"](https://sdtimes.com/data/gaining-ai-insights-from-spatial-data/). *SD Times*. Retrieved 2025-11-03.
24. [↑](./Spatial_database#cite_ref-25) ["GEOS"](http://trac.osgeo.org/geos/).
25. [↑](./Spatial_database#cite_ref-26) ["Neo4j Spatial is a library of utilities for Neo4j that facilitates the enabling of spatial operations on data. In particular you can add spatial indexes to already located data, and perform spatial"](https://github.com/neo4j-contrib/spatial). *[GitHub](./GitHub)*. 2019-02-18.
26. [↑](./Spatial_database#cite_ref-27) ["ReQL command reference - RethinkDB"](https://rethinkdb.com/api/javascript/).

 

## Further reading

 
- [Spatial Databases: A Tour](http://www.spatial.cs.umn.edu/Book/), Shashi Shekhar and Sanjay Chawla, Prentice Hall, 2003 ([ISBN](./ISBN_(identifier)) [0-13-017480-7](./Special:BookSources/0-13-017480-7))
- [Spatial Databases – With Application to GIS](http://mkp.com/books/data-management) Philippe Rigaux, Michel Scholl and Agnes Voisard. [Morgan Kaufmann Publishers](./Morgan_Kaufmann_Publishers). 2002 ([ISBN](./ISBN_(identifier)) [1-55860-588-6](./Special:BookSources/1-55860-588-6))
- [Evaluation of Data Management Systems for Geospatial Big Data](https://link.springer.com/chapter/10.1007/978-3-319-09156-3_47) Pouria Amirian, Anahid Basiri and Adam Winstanley. Springer. 2014 ([ISBN](./ISBN_(identifier)) [9783319091563](./Special:BookSources/9783319091563))

 

## External links

 
- [An introduction to PostgreSQL PostGIS](https://web.archive.org/web/20150115105621/http://www.mapbender.org/presentations/Spatial_Data_Management_Arnulf_Christl/html/)
- [PostgreSQL PostGIS as components in a Service Oriented Architecture](http://www.gisdevelopment.net/magazine/years/2006/jan/18_1.htm) [SOA](./Service-oriented_architecture)
- [A Trigger Based Security Alarming Scheme for Moving Objects on Road Networks](https://doi.org/10.1007%2F978-3-540-69304-8_11) Sajimon Abraham, P. Sojan Lal, Published by Springer Berlin / Heidelberg-2008.
- [geodatabase](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#/What_is_a_geodatabase/003n00000001000000/) ArcGIS Resource Center description of a geodatabase

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesIsrael |
| Other | Yale LUX |