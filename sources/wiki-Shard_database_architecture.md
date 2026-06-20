---
source: https://en.wikipedia.org/wiki/Shard_(database_architecture)
fetched: 2026-06-19
---

Horizontal partition of data in a database or search engine

A **database shard**, or simply a **shard**, is a [horizontal partition](./Partition_(database)#Horizontal_partitioning) of data within a [database](./DBMS) or [search engine](./Search_engine). Each shard may be held on a separate [database server](./Database_server) instance in order to spread across multiple servers.

 

Some data in a database may remain present in all shards,[[a]](./Shard_(database_architecture)#cite_note-1) while other data is stored in only one shard. In such cases, each shard acts as the single source for its subset of data.[[1]](./Shard_(database_architecture)#cite_note-2)

 

## Database architecture

 

**Horizontal partitioning** is a database design principle whereby *[rows](./Row_(database))* of a database table are held separately, rather than being split into [columns](./Column_(database)) (as in [normalization](./Database_normalization) and [vertical partitioning](./Partition_(database)), to varying degrees ). Each partition forms part of a shard, which may in turn be located on a separate database server or in a separate physical location.

 

There are numerous advantages to the horizontal partitioning of data. Since tables are divided and distributed into multiple servers, the total number of rows in each table in each database is reduced. This reduces [index](./Index_(database)) size, which generally improves search performance. A database shard can be placed on separate hardware, and multiple shards can be placed on multiple machines. This enables the distribution of a database across a large number of machines, which can significantly improve performance. In addition, if the database shard is based on some real-world segmentation of the data (e.g., European customers v. American customers) it may be possible to infer the appropriate shard membership easily and automatically, and to query only the relevant shard.[[2]](./Shard_(database_architecture)#cite_note-Rahul_Roy,_Shard-3)

 

In practice, sharding is complex. Although it has long been implemented through manual coding (especially where rows have an obvious grouping, as in the customer region example above), this approach is often inflexible. There is a desire to support sharding automatically, both in terms of adding code support for it, and for identifying candidates to be sharded separately. [Consistent hashing](./Consistent_hashing) is a technique used in sharding to distribute large loads across multiple smaller services and servers.[[3]](./Shard_(database_architecture)#cite_note-4)

 

Where [distributed computing](./Distributed_computing) is used to separate load between multiple servers (either for performance or reliability reasons), a sharding approach may also be useful. In the 2010s, sharding of [execution](./Execution_(computing)) capacity, as well as the more traditional sharding of [data](./Data_availability_(cryptography)), emerged as a potential approach to address performance and scalability challenges in [blockchains](./Blockchain).[[4]](./Shard_(database_architecture)#cite_note-acm20191021-5)[[5]](./Shard_(database_architecture)#cite_note-FCDS20200718-6)

 

Recent academic work has proposed protocols such as Cerberus to address cross-shard [atomicity](./Atomicity_(database_systems)) by braiding consensus across multiple shards, allowing transactions to affect multiple partitions simultaneously without requiring a global lock.[[6]](./Shard_(database_architecture)#cite_note-VLDB2021-7)

 

## Compared to horizontal partitioning

 

[Horizontal partitioning](./Partition_(database)#Partitioning_methods) splits one or more tables by row, usually within a *single* instance of a [schema](./Database_schema) and a database server. It may offer an advantage by reducing index size (and thus search effort), provided there is an obvious, robust, and implicit way to identify in which partition a particular row will be found, without having to first search the index; for example, the classic case of the '`CustomersEast`' and '`CustomersWest`' tables, where a [ZIP code](./ZIP_code) already indicates where a row will be found.

 

Sharding extends this approach. It partitions the relevant table or tables in the same way, but does so across potentially *multiple* instances of the schema. An advantage is that the search load for the large partitioned table can be distributed across multiple servers (logical or physical), rather than only across multiple indexes on a same logical server.

 

Splitting shards across multiple isolated instances requires more than simple horizontal partitioning. The expected gains in efficiency would be reduced if querying the database required *multiple* instances to be accessed just to retrieve a simple [dimension table](./Dimension_table). Beyond partitioning, sharding therefore involves distributing large, partitionable tables across servers, while smaller tables are replicated in full on each server.[[7]](./Shard_(database_architecture)#cite_note-8)

 

This is also why sharding is related to a [shared-nothing architecture](./Shared-nothing_architecture)—once sharded, each shard can reside in a separate logical schema instance, physical database server, [data center](./Data_center), or geographic region. Sharding is intended to minimize the need for cross-shard access by partitioning data across independent shards.[[8]](./Shard_(database_architecture)#cite_note-9)

 

This makes replication across multiple servers easier (simple horizontal partitioning does not). It is also useful for worldwide distribution of applications, where communications links between data centers might otherwise become a bottleneck.[[9]](./Shard_(database_architecture)#cite_note-10)

 

There is also a requirement for some notification and replication mechanism between schema instances, so that unpartitioned tables remain as closely synchronized as the application requires. This is a complex architectural choice in sharded systems: approaches range from making these tables effectively read-only (with updates that are rare and batched), to dynamically [replicated](./Replication_(computer_science)) tables (at the cost of reducing some of the distribution benefits of sharding), and many options in between.[[10]](./Shard_(database_architecture)#cite_note-11)

 

## Implementations

 
- [Altibase](./Altibase) provides a combined (client-side and server-side) sharding architecture transparent to client applications.
- [Apache HBase](./Apache_HBase) supports automatic sharding.[[11]](./Shard_(database_architecture)#cite_note-12)
- [Azure SQL Database Elastic Database](https://azure.microsoft.com/en-us/products/category/databases) tools support support sharding to enable scaling out and in of an application’s data tier.[[12]](./Shard_(database_architecture)#cite_note-13)
- [ClickHouse](./ClickHouse), an open-source OLAP database management system, supports sharding.
- [Couchbase](./Couchbase) supports automatic and transparent sharding.
- [CUBRID](./CUBRID) has supported sharding since version 9.0.
- [Db2 Data Partitioning Feature (MPP)](https://help.sap.com/docs/DB6/4c49a344277943ad91358094fdaf9765/c289a552d161224fe10000000a445394.html), a shared-nothing database partitioning feature, runs on separate nodes.
- [DRDS (Distributed Relational Database Service)](https://www.alibabacloud.com/blog/what-are-the-differences-between-polardb-x-and-drds_601253) of [Alibaba Cloud](./Alibaba_Cloud) supports database and table sharding,[[13]](./Shard_(database_architecture)#cite_note-14) and has been used for large-scale events such as [Singles' Day](./Singles'_Day).[[14]](./Shard_(database_architecture)#cite_note-15)
- [Elasticsearch](./Elasticsearch), an enterprise search server, supports sharding.[[15]](./Shard_(database_architecture)#cite_note-Elasticsearch_Shard-16)
- [eXtreme Scale](./IBM_WebSphere_eXtreme_Scale) is a cross-process in-memory key/value data store (a [NoSQL](./NoSQL) data store) that uses sharding to achieve scalability across processes for both data and [MapReduce](./MapReduce)-style parallel processing.[[16]](./Shard_(database_architecture)#cite_note-17)
- [Hibernate](./Hibernate_(Java)) supports sharding, but has seen little development since 2007.[[17]](./Shard_(database_architecture)#cite_note-Hibernate_Shards-18)[[18]](./Shard_(database_architecture)#cite_note-Hibernate_Shards_documentation-19)
- [IBM Informix](./Informix) has supported sharding since version 12.1 xC1 as part of the MACH11 technology. Informix 12.10 xC2 added full compatibility with MongoDB drivers, allowing a mix of regular relational tables and NoSQL collections while retaining sharding, fail-over, and ACID properties.[[19]](./Shard_(database_architecture)#cite_note-Informix_Grid_Queries-20)[[20]](./Shard_(database_architecture)#cite_note-NoSQL_support_in_Informix-21)
- [Kdb+](./Kdb+) has supported sharding since version 2.0.
- [MariaDB](./MariaDB) Spider, a storage engine, supports table federation, sharding, XA transactions, and ODBC data sources. It has been included in MariaDB server since version 10.0.4.[[21]](./Shard_(database_architecture)#cite_note-22)
- [MonetDB](./MonetDB), an open-source [column-store](./Column-oriented_DBMS), introduced read-only sharding in its July 2015 release.[[22]](./Shard_(database_architecture)#cite_note-23)
- [MongoDB](./MongoDB) has supported sharding since version 1.6.[[23]](./Shard_(database_architecture)#cite_note-24)
- [MySQL Cluster](./MySQL_Cluster) supports automatic and transparent sharding across commodity nodes, allowing scaling of read and write queries, without requiring application changes.[[24]](./Shard_(database_architecture)#cite_note-MySQL_Cluster_Features_&_Benefits-25)
- [MySQL](./MySQL) Fabric (part of MySQL utilities) supports sharding.[[25]](./Shard_(database_architecture)#cite_note-MySQL_Fabric_sharding_quick_start_guide-26)
- [Oracle Database](./Oracle_Database) shards since 12c Release 2 and in one liner: Combination of sharding advantages with well-known capabilities of enterprise ready multi-model Oracle Database.[[26]](./Shard_(database_architecture)#cite_note-Oracle_2018-27)
- [Oracle NoSQL Database](./Oracle_NoSQL_Database) supports automatic sharding and elastic, online expansion of clusters.
- [OrientDB](./OrientDB) has supported sharding since version 1.7.
- [Solr](./Solr), an enterprise search platform, supports sharding.[[27]](./Shard_(database_architecture)#cite_note-SorlShard-28)
- [ScyllaDB](./ScyllaDB) uses per-core sharding within a server and across all nodes in a cluster.
- [Spanner](./Spanner_(database)), a distributed database developed by Google, shards across multiple [Paxos](./Paxos_(computer_science)) state machines to scale to large numbers of machines, data centers, and rows.[[28]](./Shard_(database_architecture)#cite_note-Spanner-29)
- [SQLAlchemy ORM](./SQLAlchemy), a data-mapper for the [Python programming language](./Python_(programming_language)) shards.[[29]](./Shard_(database_architecture)#cite_note-SQLAlchemy-30)
- [SQL Server](./SQL_Server_(disambiguation)) has supported sharding since SQL Server 2005 with the use of 3rd party tools.[[30]](./Shard_(database_architecture)#cite_note-SQLServer-31)
- [Teradata](./Teradata) markets a massive parallel database management system as a [data warehouse](./Data_warehouse).
- [Vault](https://www.ndss-symposium.org/ndss-paper/vault-fast-bootstrapping-for-the-algorand-cryptocurrency/), a [cryptocurrency](./Cryptocurrency) design, uses sharding to reduce the data required to join the network and verify transactions, improving scalability.[[31]](./Shard_(database_architecture)#cite_note-32)
- [Vitess](./Cloud_Native_Computing_Foundation#Vitess), an open-source database clustering system, supports sharding for MySQL and is a [Cloud Native Computing Foundation](./Cloud_Native_Computing_Foundation) project.[[32]](./Shard_(database_architecture)#cite_note-Vitess-33)
- [ShardingSphere](https://shardingsphere.apache.org) is a database clustering system that provides data sharding, distributed transactions, and distributed database management, and is an [Apache Software Foundation](./Apache_Software_Foundation) (ASF) project.[[33]](./Shard_(database_architecture)#cite_note-ShardingSphere-34)

 

## Disadvantages

 

Sharding a database table before it has been optimized locally can introduce unnecessary complexity. Sharding is generally recommended when other optimization strategies have proven insufficient.[[34]](./Shard_(database_architecture)#cite_note-35) The added complexity of database sharding can result in several potential challenges.[[35]](./Shard_(database_architecture)#cite_note-36)

 
- SQL complexity: Developers may need to write more complex SQL queries to handle sharding logic
- Additional software requirements: Software that partitions, balances, coordinates, and maintains data integrity can fail or introduce errors.
- [Single point of failure](./Single_point_of_failure): Corruption or failure of one shard due to network, hardware, or system issues can affect the integrity of the entire dataset.
- [Fail-over](./Fail-over) server complexity: Fail-over servers must maintain copies of all database shards.
- [Backups](./Backup) complexity: Database backups of the individual shards must be coordinated with the backups of the other shards.
- Operational complexity: Tasks such as adding or removing indexes, modifying columns, or altering the schema become more difficult in a sharded environment.

 

## Etymology

 

In a database context, the term "shard" is believed to derive from one of two sources: [Computer Corporation of America](./Computer_Corporation_of_America)'s "A System for Highly Available Replicated Data,"[[36]](./Shard_(database_architecture)#cite_note-37) which used redundant hardware to facilitate data replication rather than horizontal partitioning, or the 1997 [MMORPG](./MMORPG) *[Ultima Online](./Ultima_Online)*.[[37]](./Shard_(database_architecture)#cite_note-koster-38)[[38]](./Shard_(database_architecture)#cite_note-garriott-39)

 

[Richard Garriott](./Richard_Garriott), creator of *Ultima Online*, recalled that the term originated during the production of the game, specifically in creating a self-regulating, virtual ecology system. Players were able to interact and harvest in-game resources via the internet, which disrupted the balance of the system.[[38]](./Shard_(database_architecture)#cite_note-garriott-39) To address this, the development team separated the global player base into multiple sessions and introduced part of *Ultima Online*'s fictional connection to the end of *[Ultima I: The First Age of Darkness](./Ultima_I:_The_First_Age_of_Darkness)*, where the defeat of its antagonist [Mondain](./Mondain) also led to the creation of [multiverse](./Multiverse) "shards." This modification provided Garriott's team with the fictional basis needed to justify creating copies of the virtual environment. The feature was later removed after several months of testing.[[38]](./Shard_(database_architecture)#cite_note-garriott-39)

 

## See also

 
- [Block Range Index](./Block_Range_Index)
- [Shared-nothing architecture](./Shared-nothing_architecture)

 

## Notes

  
1. [↑](./Shard_(database_architecture)#cite_ref-1) Typically supporting data such as [dimension tables](./Dimension_table).

 

## References

  
1. [↑](./Shard_(database_architecture)#cite_ref-2) Sadalage, Pramod J.; [Fowler, Martin](./Martin_Fowler_(software_engineer)) (2012). "4: Distribution Models". *NoSQL Distilled*. Pearson Education. [ISBN](./ISBN_(identifier)) [978-0321826626](./Special:BookSources/978-0321826626).
2. [↑](./Shard_(database_architecture)#cite_ref-Rahul_Roy,_Shard_3-0) Rahul Roy (July 28, 2008). ["Shard - A Database Design"](http://technoroy.blogspot.com/2008/07/shard-database-design.html). 
3. [↑](./Shard_(database_architecture)#cite_ref-4) Ries, Eric. ["Sharding for Startups"](http://www.startuplessonslearned.com/2009/01/sharding-for-startups.html).
4. [↑](./Shard_(database_architecture)#cite_ref-acm20191021_5-0) Wang, Gang; Shi, Zhijie Jerry; Nixon, Mark; Han, Song (21 October 2019). ["SoK"](https://dl.acm.org/doi/abs/10.1145/3318041.3355457). *Proceedings of the 1st ACM Conference on Advances in Financial Technologies*. pp. 41–61. [doi](./Doi_(identifier)):[10.1145/3318041.3355457](https://doi.org/10.1145%2F3318041.3355457). [ISBN](./ISBN_(identifier)) [9781450367325](./Special:BookSources/9781450367325). [S2CID](./S2CID_(identifier)) [204749727](https://api.semanticscholar.org/CorpusID:204749727).
5. [↑](./Shard_(database_architecture)#cite_ref-FCDS20200718_6-0) Yu, Mingchao; Sahraei, Saeid; Nixon, Mark; Han, Song (18 July 2020). "SoK: Sharding on Blockchain". [*Proceedings of the 1st ACM Conference on Advances in Financial Technologies*](https://dl.acm.org/doi/abs/10.1145/3318041.3355457). pp. 114–134. [doi](./Doi_(identifier)):[10.1145/3318041.3355457](https://doi.org/10.1145%2F3318041.3355457). [ISBN](./ISBN_(identifier)) [9781450367325](./Special:BookSources/9781450367325). [S2CID](./S2CID_(identifier)) [204749727](https://api.semanticscholar.org/CorpusID:204749727).
6. [↑](./Shard_(database_architecture)#cite_ref-VLDB2021_7-0) Hellings, Jelle; Sadoghi, Mohammad (2021). ["Cerberus: Minimalistic Multi-shard Byzantine-resilient Transaction Processing"](http://www.vldb.org/pvldb/vol14/p2230-hellings.pdf) (PDF). *Proceedings of the VLDB Endowment*. **14** (11): 2230–2243. [doi](./Doi_(identifier)):[10.14778/3476249.3476274](https://doi.org/10.14778%2F3476249.3476274).
7. [↑](./Shard_(database_architecture)#cite_ref-8) ["Database Sharding: Concepts & Examples"](https://www.mongodb.com/resources/products/capabilities/database-sharding-explained). *MongoDB*. Retrieved 2026-03-20.
8. [↑](./Shard_(database_architecture)#cite_ref-9) ["Understanding Database Sharding"](https://www.digitalocean.com/community/tutorials/understanding-database-sharding). *DigitalOcean Community Tutorials*. 2022-03-16. Retrieved 2025-10-09. Database shards exemplify a shared-nothing architecture. This means that the shards are autonomous; they don't share any of the same data or resources.
9. [↑](./Shard_(database_architecture)#cite_ref-10) ["A Guide To Horizontal Vs Vertical Scaling"](https://www.mongodb.com/resources/basics/horizontal-vs-vertical-scaling). *MongoDB*. Retrieved 2026-03-20.
10. [↑](./Shard_(database_architecture)#cite_ref-11) ["Sharding - Database Manual - MongoDB Docs"](https://www.mongodb.com/docs/manual/sharding/). *www.mongodb.com*. Retrieved 2026-03-20.
11. [↑](./Shard_(database_architecture)#cite_ref-12) ["Apache HBase – Apache HBase™ Home"](https://hbase.apache.org/). *hbase.apache.org*.
12. [↑](./Shard_(database_architecture)#cite_ref-13) ["Introducing Elastic Scale preview for Azure SQL Database"](https://azure.microsoft.com/en-us/blog/introducing-elastic-scale-preview-for-azure-sql-database/). *azure.microsoft.com*. 2 October 2014.
13. [↑](./Shard_(database_architecture)#cite_ref-14) ["Alibaba Cloud Help Center - Cloud Definition and Explanation of Cloud Based Services - Alibaba Cloud"](https://www.alibabacloud.com/help/doc-detail/29659.htm?spm=a2c63.l28256.a3.1.4eb21d9a8lUMTW). *www.alibabacloud.com*.
14. [↑](./Shard_(database_architecture)#cite_ref-15) ["Focuses on Large-Scale Online Databases - Alibaba Cloud"](https://www.alibabacloud.com/product/drds). *www.alibabacloud.com*.
15. [↑](./Shard_(database_architecture)#cite_ref-Elasticsearch_Shard_16-0) ["Index Shard Allocation | Elasticsearch Guide [7.13] | Elastic"](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules-allocation.html). *www.elastic.co*.
16. [↑](./Shard_(database_architecture)#cite_ref-17) ["IBM Docs"](http://publib.boulder.ibm.com/infocenter/wxsinfo/v7r1/index.jsp?topic=%2Fcom.ibm.websphere.extremescale.over.doc%2).
17. [↑](./Shard_(database_architecture)#cite_ref-Hibernate_Shards_18-0) ["Hibernate Shards"](http://shards.hibernate.org/). 2007-02-08.
18. [↑](./Shard_(database_architecture)#cite_ref-Hibernate_Shards_documentation_19-0) ["Hibernate Shards"](https://web.archive.org/web/20081216005922/http://www.hibernate.org/hib_docs/shards/reference/en/html/). Archived from [the original](http://www.hibernate.org/hib_docs/shards/reference/en/html/) on 2008-12-16. Retrieved 2011-03-30.
19. [↑](./Shard_(database_architecture)#cite_ref-Informix_Grid_Queries_20-0) ["New Grid queries for Informix"](https://web.archive.org/web/20150610221958/http://ibmdatamag.com/2013/04/informix-12-10-new-grid-queries/). Archived from [the original](http://ibmdatamag.com/2013/04/informix-12-10-new-grid-queries/) on 2015-06-10. Retrieved 2013-10-07.
20. [↑](./Shard_(database_architecture)#cite_ref-NoSQL_support_in_Informix_21-0) ["NoSQL support in Informix (JSON storage, Mongo DB API)"](https://fr.slideshare.net/journalofinformix/informix-no-sql-sept-2013). September 24, 2013.
21. [↑](./Shard_(database_architecture)#cite_ref-22) ["Spider"](https://mariadb.com/kb/en/spider/). *MariaDB KnowledgeBase*. Retrieved 2022-12-20.
22. [↑](./Shard_(database_architecture)#cite_ref-23) ["MonetDB July2015 Released"](https://www.monetdb.org/blog/monetdb-jul2015-released). 31 August 2015.
23. [↑](./Shard_(database_architecture)#cite_ref-24) ["MongoDB Sharding"](https://www.mongodb.com/resources/products/capabilities/sharding). *MongoDB*. Retrieved 2026-03-20.
24. [↑](./Shard_(database_architecture)#cite_ref-MySQL_Cluster_Features_&_Benefits_25-0) ["MySQL Cluster Features & Benefits"](http://www.mysql.com/products/cluster/features.html). 2012-11-23.
25. [↑](./Shard_(database_architecture)#cite_ref-MySQL_Fabric_sharding_quick_start_guide_26-0) ["MySQL Fabric sharding quick start guide"](http://dev.mysql.com/doc/mysql-utilities/1.5/en/fabric-quick-start-sharding.html).
26. [↑](./Shard_(database_architecture)#cite_ref-Oracle_2018_27-0) ["Oracle Sharding"](https://www.oracle.com/database/technologies/high-availability/sharding.html). *Oracle*. 2018-05-24. Retrieved 2021-07-10.
27. [↑](./Shard_(database_architecture)#cite_ref-SorlShard_28-0) ["DistributedSearch - SOLR - Apache Software Foundation"](https://cwiki.apache.org/confluence/display/solr/DistributedSearch). *cwiki.apache.org*.
28. [↑](./Shard_(database_architecture)#cite_ref-Spanner_29-0) Corbett, James C; Dean, Jeffrey; Epstein, Michael; Fikes, Andrew; Frost, Christopher; Furman, JJ; Ghemawat, Sanjay; Gubarev, Andrey; Heiser, Christopher; Hochschild, Peter; Hsieh, Wilson; Kanthak, Sebastian; Kogan, Eugene; Li, Hongyi; Lloyd, Alexander; Melnik, Sergey; Mwaura, David; Nagle, David; Quinlan, Sean; Rao, Rajesh; Rolig, Lindsay; Saito, Yasushi; Szymaniak, Michal; Taylor, Christopher; Wang, Ruth; Woodford, Dale. ["Spanner: Google's Globally-Distributed Database"](http://research.google.com/archive/spanner-osdi2012.pdf) (PDF). *Proceedings of OSDI 2012*. Retrieved 24 February 2014.
29. [↑](./Shard_(database_architecture)#cite_ref-SQLAlchemy_30-0) ["sqlalchemy/sqlalchemy"](https://github.com/sqlalchemy/sqlalchemy). July 9, 2021 – via GitHub.
30. [↑](./Shard_(database_architecture)#cite_ref-SQLServer_31-0) ["Partitioning and Sharding Options for SQL Server and SQL Azure"](https://www.infoq.com/news/2011/02/SQL-Sharding/). *infoq.com*.
31. [↑](./Shard_(database_architecture)#cite_ref-32) ["A faster, more efficient cryptocurrency"](https://news.mit.edu/2019/vault-faster-more-efficient-cryptocurrency-0124). *MIT News*. 24 January 2019. Retrieved 2019-01-30.
32. [↑](./Shard_(database_architecture)#cite_ref-Vitess_33-0) ["Vitess"](https://vitess.io/). *vitess.io*.
33. [↑](./Shard_(database_architecture)#cite_ref-ShardingSphere_34-0) ["ShardingSphere"](https://shardingsphere.apache.org/). *shardingsphere.apache.org*.
34. [↑](./Shard_(database_architecture)#cite_ref-35) Kleppmann, Martin (2017). *Designing Data-Intensive Applications*. [ISBN](./ISBN_(identifier)) [9781449373320](./Special:BookSources/9781449373320).
35. [↑](./Shard_(database_architecture)#cite_ref-36) ["Database Sharding: Concepts & Examples"](https://www.mongodb.com/resources/products/capabilities/database-sharding-explained). *MongoDB*. Retrieved 2026-03-20.
36. [↑](./Shard_(database_architecture)#cite_ref-37) Sarin, DeWitt & Rosenberg, *Overview of SHARD: A System for Highly Available Replicated Data*, Technical Report CCA-88-01, Computer Corporation of America, May 1988
37. [↑](./Shard_(database_architecture)#cite_ref-koster_38-0) Koster, Raph (2009-01-08). ["Database "sharding" came from UO?"](http://www.raphkoster.com/2009/01/08/database-sharding-came-from-uo/). *Raph Koster's Website*. Retrieved 2015-01-17.
38. [1](./Shard_(database_architecture)#cite_ref-garriott_39-0) [2](./Shard_(database_architecture)#cite_ref-garriott_39-1) [3](./Shard_(database_architecture)#cite_ref-garriott_39-2) ["Ultima Online: The Virtual Ecology | War Stories"](https://www.youtube.com/watch?v=KFNxJVTJleE). *Ars Technica Videos*. 21 December 2017.

 

## External links

 
- [Informix JSON data sharding](https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.json.doc/ids_json_011.htm)

 
| vteDatabase management systems |
| --- |
| Types | Object-orientedcomparisonRelationallistcomparisonKey–valueColumn-orientedlistDocument-orientedWide-column storeGraphNoSQLNewSQLIn-memorylistMulti-modelcomparisonCloudBlockchain-based database |
| Concepts | DatabaseACIDArmstrong's axiomsCodd's 12 rulesCAP theoremCRUDNullCandidate keyForeign keyPACELC design principleSuperkeySurrogate keyUnique key |
| Objects | RelationtablecolumnrowViewTransactionTransaction logTriggerIndexStored procedureCursorPartition |
| Components | Concurrency controlData dictionaryJDBCXQJODBCQuery languageQuery optimizerQuery rewriting systemQuery plan |
| Functions | AdministrationQuery optimizationReplicationSharding |
| Related topics | Database modelsDatabase normalizationDatabase storageDistributed databaseFederated database systemReferential integrityRelational algebraRelational calculusRelational modelObject–relational databaseTransaction processingList of SQL software and tools |
| CategoryOutline |

 
| vteSoftware design patterns |
| --- |
| Gang of Fourpatterns | CreationalAbstract factoryBuilderFactory methodPrototypeSingletonStructuralAdapterBridgeCompositeDecoratorFacadeFlyweightProxyBehavioralChain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor | Creational | Abstract factoryBuilderFactory methodPrototypeSingleton | Structural | AdapterBridgeCompositeDecoratorFacadeFlyweightProxy | Behavioral | Chain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor |
| Creational | Abstract factoryBuilderFactory methodPrototypeSingleton |
| Structural | AdapterBridgeCompositeDecoratorFacadeFlyweightProxy |
| Behavioral | Chain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor |
| Concurrencypatterns | Active objectBalkingBinding propertiesDouble-checked lockingEvent-based asynchronousGuarded suspensionJoinLockMonitorProactorReactorRead–write lockSchedulerScheduled-task patternSemaphoreThread poolThread-local storage |
| Architecturalpatterns | Front controllerInterceptorMVCMVPMVVMADRECSn-tierSpecificationPublish–subscribeNaked objectsService locatorActive recordIdentity mapData access object (DAO)Data transfer object (DTO)Inversion of controlModel 2Broker |
| Otherpatterns | BlackboardBusiness delegateComposite entityComposition over inheritanceDependency injectionGuard clauseIntercepting filterLazy loadingMock objectNull objectObject poolServantTwinType tunnelMethod chainingDelegation |
| Books | Design PatternsEnterprise Integration Patterns |
| People | Christopher AlexanderErich GammaRalph JohnsonJohn VlissidesGrady BoochKent BeckWard CunninghamMartin FowlerRobert MartinJim CoplienDouglas SchmidtLinda Rising |
| Communities | The Hillside GroupPortland Pattern Repository |
| See also | Anti-patternArchitectural pattern |