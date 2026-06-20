---
source: https://en.wikipedia.org/wiki/Object_storage
fetched: 2026-06-19
---

Computer data storage architecture that manages data as objects 

**Object storage** (also known as **object-based storage**[[1]](./Object_storage#cite_note-1) or **blob storage**) is a [computer data storage](./Computer_data_storage) approach that manages data as "blobs" or "objects", as opposed to other storage architectures like [file systems](./File_systems), which manage data as a file hierarchy, and [block storage](./Block_storage), which manages data as blocks within sectors and tracks.[[2]](./Object_storage#cite_note-2) Each object is typically associated with a variable amount of [metadata](./Metadata), and a [globally unique identifier](./Globally_unique_identifier). Object storage can be implemented at multiple levels, including the device level (object-storage device), the system level, and the interface level. In each case, object storage seeks to enable capabilities not addressed by other storage architectures, like interfaces that are directly programmable by the application, a namespace that can span multiple instances of physical hardware, and data-management functions like [data replication](./Data_replication) and data distribution at object-level granularity.

 

Object storage systems allow retention of massive amounts of [unstructured data](./Unstructured_data) in which data is written once and read once (or many times).[[3]](./Object_storage#cite_note-objectstorage-3) Object storage is used for purposes such as storing objects like videos and photos on [Facebook](./Facebook), songs on [Spotify](./Spotify), or files in online collaboration services, such as [Dropbox](./Dropbox_(service)).[[4]](./Object_storage#cite_note-4) One of the limitations with object storage is that it is not intended for [transactional data](./Transactional_data), as object storage was not designed to replace [NAS](./Network-attached_storage) file access and sharing; it does not support the locking and sharing mechanisms needed to maintain a single, accurately updated version of a file.[[3]](./Object_storage#cite_note-objectstorage-3)

 

## History

 

### Origins

 

[Jim Starkey](./Jim_Starkey) coined the term ***blob***[*[when?](./Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items)*] working at [Digital Equipment Corporation](./Digital_Equipment_Corporation) to refer to opaque data entities.  The terminology was adopted for [Rdb/VMS](./Rdb/VMS).  *Blob* is often humorously explained to be an abbreviation for *binary large object*.   According to Starkey, this [backronym](./Backronym) arose when Terry McKiever, working in marketing at [Apollo Computer](./Apollo_Computer) felt that the term needed to be an abbreviation.  McKiever began using the expansion *basic large object*.  This was later eclipsed by the retroactive explanation of blobs as *binary large objects*.  According to Starkey, "Blob don't stand for nothin'."  Rejecting the acronym, he explained his motivation behind the coinage, saying, "A blob is the thing that ate Cincinnatti [*[sic](./Sic)*], Cleveland, or whatever", referring to the 1958 science fiction film *[The Blob](./The_Blob)*.[[5]](./Object_storage#cite_note-true-story-5)

 

In 1995, research led by [Garth Gibson](./Garth_Gibson) on [Network-Attached Secure Disks](./Network-Attached_Secure_Disks) first promoted the concept of splitting less common operations, like namespace manipulations, from common operations, like reads and writes, to optimize the performance and scale of both.[[6]](./Object_storage#cite_note-NASD-6)  In the same year, a Belgian company – FilePool – was established to build the basis for archiving functions. Object storage was proposed at Gibson's [Carnegie Mellon University](./Carnegie_Mellon_University) lab as a research project in 1996.[[7]](./Object_storage#cite_note-7)   Another key concept was abstracting the writes and reads of data to more flexible data containers (objects). Fine grained access control through object storage architecture[[8]](./Object_storage#cite_note-8)  was further described by one of the NASD team, Howard Gobioff, who later was one of the inventors of the [Google File System](./Google_File_System).[[9]](./Object_storage#cite_note-9)

 

Other related work includes the [Coda](./Coda_(file_system)) filesystem project at [Carnegie Mellon](./Carnegie_Mellon), which started in 1987, and spawned the [Lustre file system](./Lustre_(file_system)).[[10]](./Object_storage#cite_note-Lustre-10) There is also the OceanStore project at UC Berkeley,[[11]](./Object_storage#cite_note-11) which started in 1999[[12]](./Object_storage#cite_note-12) and the Logistical Networking project at the University of Tennessee Knoxville, which started in 1998.[[13]](./Object_storage#cite_note-13) In 1999, Gibson founded [Panasas](./Panasas) to commercialize the concepts developed by the NASD team.

 

### Development

 

[Seagate Technology](./Seagate_Technology) played a central role in the development of object storage. According to the [Storage Networking Industry Association](./Storage_Networking_Industry_Association) (SNIA), "Object storage originated in the late 1990s: Seagate specifications from 1999 Introduced some of the first commands and how operating system effectively removed from consumption of the storage."[[14]](./Object_storage#cite_note-14)

 

A preliminary version of the "OBJECT BASED STORAGE DEVICES Command Set Proposal" dated 10/25/1999 was submitted by Seagate as edited by Seagate's Dave Anderson and was the product of work by the National Storage Industry Consortium (NSIC) including contributions by [Carnegie Mellon University](./Carnegie_Mellon_University), Seagate, IBM, [Quantum](./Quantum_Corporation), and [StorageTek](./StorageTek).[[15]](./Object_storage#cite_note-15) This paper was proposed to INCITS T-10 ([International Committee for Information Technology Standards](./International_Committee_for_Information_Technology_Standards)) with a goal to form a committee and design a specification based on the SCSI interface protocol. This defined objects as abstracted data, with unique identifiers and metadata, how objects related to file systems, along with many other innovative concepts. Anderson presented many of these ideas at the SNIA conference in October 1999. The presentation revealed an IP Agreement that had been signed in February 1997 between the original collaborators (with Seagate represented by Anderson and Chris Malakapalli) and covered the benefits of object storage, scalable computing, platform independence, and storage management.[[16]](./Object_storage#cite_note-16)

 

## Architecture

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5d/High_level_object_storage_architecture.svg/250px-High_level_object_storage_architecture.svg.png)](./File:High_level_object_storage_architecture.svg) 

### Abstraction of storage

 

One of the design principles of object storage is to abstract some of the lower layers of storage away from the administrators and applications. Thus, data is exposed and managed as objects instead of [blocks](./Block_(data_storage)) or (exclusively) files. Objects contain additional descriptive properties which can be used for better indexing or management. Administrators do not have to perform lower-level storage functions like constructing and managing [logical volumes](./Logical_unit_number) to utilize disk capacity or setting [RAID](./RAID) levels to deal with disk failure.

 

Object storage also allows the addressing and identification of individual objects by more than just file name and file path. Object storage adds a unique identifier within a bucket, or across the entire system, to support much larger namespaces and eliminate name collisions.

 

### Inclusion of rich custom metadata within the object

 

Object storage explicitly separates file metadata from data to support additional capabilities.
As opposed to fixed metadata in file systems (filename, creation date, type, etc.), object storage provides for full function, custom, object-level metadata in order to:

 
- Capture application-specific or user-specific information for better indexing purposes
- Support data-management policies (e.g. a policy to drive object movement from one storage tier to another)
- Centralize management of storage across many individual nodes and clusters
- Optimize metadata storage (e.g. encapsulated, database or key value storage) and caching/indexing (when authoritative metadata is encapsulated with the metadata inside the object) independently from the data storage (e.g. unstructured binary storage)

 

Additionally, in some object-based file-system implementations:

 
- The file system clients only contact metadata servers once when the file is opened and then get content directly via object-storage servers (vs. block-based file systems which would require constant metadata access)
- Data objects can be configured on a per-file basis to allow adaptive stripe width, even across multiple object-storage servers, supporting optimizations in bandwidth and I/O

 

**Object-based storage devices** (**OSD**) as well as some software implementations (e.g., DataCore Swarm) manage metadata and data at the storage device level:

 
- Instead of providing a block-oriented interface that reads and writes fixed sized blocks of data, data is organized into flexible-sized data containers, called objects
- Each object has both data (an uninterpreted sequence of bytes) and metadata (an extensible set of attributes describing the object); physically encapsulating both together benefits recoverability.
- The command interface includes commands to create and delete objects, write bytes and read bytes to and from individual objects, and to set and get attributes on objects
- Security mechanisms provide per-object and per-command access control

 

### Programmatic data management

 

Object storage provides programmatic interfaces to allow applications to manipulate data. At the base level, this includes Create, read, update and delete ([CRUD](./CRUD)) functions for basic read, write and delete operations. Some object storage implementations go further, supporting additional functionality like [object/file versioning](./Versioning_file_system#Similar_technologies), object replication, life-cycle management and movement of objects between different tiers and types of storage. Most API implementations are [REST](./REST)-based, allowing the use of many standard [HTTP](./HTTP) calls.

 

## Implementation

 

### Cloud storage

 Main article: [Cloud storage](./Cloud_storage) 

The vast majority of cloud storage available in the market leverages an object-storage architecture. Some notable examples are [Amazon S3](./Amazon_S3), which debuted in March 2006, [Microsoft Azure](./Microsoft_Azure) Blob Storage, [IBM Cloud Object Storage](./IBM_Cloud_Object_Storage), [Rackspace Cloud Files](./Rackspace_Cloud_Files) (whose code was donated in 2010 to Openstack project and released as [OpenStack Swift](./OpenStack#Swift)), and [Google Cloud Storage](./Google_Cloud_Storage) released in May 2010.

 

### Object-based file systems

 

Some distributed file systems use an object-based architecture, where file metadata is stored in metadata servers and file data is stored in object storage servers. File system client software interacts with the distinct servers, and abstracts them to present a full file system to users and applications.

 

### Object-storage systems

 

Some early incarnations of object storage were used for archiving, as implementations were optimized for data services like immutability, not performance. [EMC Centera](./Content-addressable_storage) and Hitachi HCP (formerly known as HCAP) are two commonly cited object storage products for archiving. Another example is [Quantum](./Quantum_Corporation) ActiveScale Object Storage Platform.

 

More general-purpose object-storage systems came to market around 2008. Lured by the incredible growth of "captive" storage systems within web applications like Yahoo Mail and the early success of cloud storage, object-storage systems promised the scale and capabilities of cloud storage, with the ability to deploy the system within an enterprise, or at an aspiring cloud-storage service provider.

 

### Unified file and object storage

 

A few object-storage systems support Unified File and Object storage, allowing clients to store objects on a storage system while simultaneously other clients store files on the same storage system.[[17]](./Object_storage#cite_note-pritchard1-17) Other vendors in the area of [Hybrid cloud storage](./Hybrid_cloud_storage) are using [Cloud storage gateways](./Cloud_storage_gateway) to provide a file access layer over object storage, implementing file access protocols such as SMB and NFS.

 

### "Captive" object storage

 

Some large Internet companies developed their own software when object-storage products were not commercially available or use cases were very specific. Facebook famously invented their own object-storage software, code-named Haystack, to address their particular massive-scale photo management needs efficiently.[[18]](./Object_storage#cite_note-haystack-18)

 

### Object-based storage devices

 

Object storage at the protocol and device layer was proposed 20 years ago[*[ambiguous](./Wikipedia:Please_clarify)*] and approved for the [SCSI](./SCSI) command set nearly 10 years ago[*[ambiguous](./Wikipedia:Please_clarify)*] as "Object-based Storage Device Commands" (OSD),[[19]](./Object_storage#cite_note-19) however, it had not been put into production until the development of the Seagate Kinetic Open Storage platform.[[20]](./Object_storage#cite_note-20)[[21]](./Object_storage#cite_note-21)  The [SCSI](./SCSI) command set for Object Storage Devices was developed by a working group of the SNIA for the T10 committee of the [International Committee for Information Technology Standards](./International_Committee_for_Information_Technology_Standards) (INCITS).[[22]](./Object_storage#cite_note-22)  T10 is responsible for all SCSI standards.

 

## Market adoption

 

One of the first object-storage products, [Lustre](./Lustre_(file_system)), is used in 70% of the Top 100 supercomputers and ~50% of the [Top 500](./Top_500).[[23]](./Object_storage#cite_note-23) As of June 16, 2013, this includes 7 of the top 10, including the current fourth fastest system on the list - China's Tianhe-2 and the seventh fastest, the [Titan supercomputer](./Titan_(supercomputer)) at the [Oak Ridge National Laboratory](./Oak_Ridge_National_Laboratory).[[24]](./Object_storage#cite_note-24)

 

Object-storage systems had good adoption in the early 2000s as an archive platform, particularly in the wake of compliance laws like [Sarbanes-Oxley](./Sarbanes-Oxley). After five years in the market, EMC's Centera product claimed over 3,500 customers and 150 [petabytes](./Petabytes) shipped by 2007.[[25]](./Object_storage#cite_note-25) Hitachi's HCP product also claims many [petabyte](./Petabyte)-scale customers.[[26]](./Object_storage#cite_note-26) Newer object storage systems have also gotten some traction, particularly around very large custom applications like eBay's auction site, where EMC Atmos is used to manage over 500 million objects a day.[[27]](./Object_storage#cite_note-27) As of March 3, 2014, EMC claims to have sold over 1.5 exabytes of Atmos storage.[[28]](./Object_storage#cite_note-28) On July 1, 2014, [Los Alamos National Lab](./Los_Alamos_National_Lab) chose the [Scality RING](./Scality) as the basis for a 500-petabyte storage environment, which would be among the largest ever.[[29]](./Object_storage#cite_note-29)

 

"Captive" object storage systems like Facebook's Haystack have scaled impressively. In April 2009, Haystack was managing 60 billion photos and 1.5 petabytes of storage, adding 220 million photos and 25 terabytes a week.[[18]](./Object_storage#cite_note-haystack-18) Facebook more recently stated that they were adding 350 million photos a day and were storing 240 billion photos.[[30]](./Object_storage#cite_note-30) This could equal as much as 357 petabytes.[[31]](./Object_storage#cite_note-31)

 

Cloud storage has become pervasive as many new web and mobile applications choose it as a common way to store [binary data](./Binary_data).[[32]](./Object_storage#cite_note-32)  As the storage back-end to many popular applications like [Smugmug](./Smugmug) and [Dropbox](./Dropbox_(service)), [Amazon S3](./Amazon_S3) has grown to massive scale, citing over 2-trillion objects stored in April 2013.[[33]](./Object_storage#cite_note-33) Two months later, Microsoft claimed that they stored even more objects in Azure at 8.5 trillion.[[34]](./Object_storage#cite_note-34) By April 2014, Azure claimed over 20-trillion objects stored.[[35]](./Object_storage#cite_note-35) Windows Azure Storage manages Blobs (user files), Tables (structured storage), and Queues (message delivery) and counts them all as objects.[[36]](./Object_storage#cite_note-36)

 

## Market analysis

 

Coldago Research which publishes an annual evaluation report of the object storage in its 2024 report titled *Coldago Research Map 2024 for Object Storage*, gave an insight into innovations, market dynamics and future direction of object storage characterized by its rapid evolution, growing adoption, and expanding set of enterprise use cases. Coldago Research adopted qualitative and quantitative analysis of the object storage market to rank 13 notable vendors based on technological capabilities, market momentum, and innovation trajectory.[[37]](./Object_storage#cite_note-37)

 

The 2024 Coldago object storage market leader rating is in alphabetical order: [Cloudian](./Cloudian), [DataCore](./DataCore), [Dell EMC](./EMC_Corporation), [Huawei](./Huawei), [IBM](./IBM), [MinIO](./MinIO), [Pure Storage](./Pure_Storage), [Quantum](./Quantum_Corporation), and [VAST Data](./VAST_Data).[[38]](./Object_storage#cite_note-38)

 

## Standards

 

### Object-based storage device standards

 

#### OSD version 1

 

In the first version of the OSD standard,[[39]](./Object_storage#cite_note-39) objects are specified with a 64-bit partition ID and a 64-bit object ID. Partitions are created and deleted within an OSD, and objects are created and deleted within partitions. There are no fixed sizes associated with partitions or objects; they are allowed to grow subject to physical size limitations of the device or logical quota constraints on a partition.

 

An extensible set of attributes describe objects. Some attributes are implemented directly by the OSD, such as the number of bytes in an object and the modification time of an object. There is a special policy tag attribute that is part of the security mechanism. Other attributes are uninterpreted by the OSD. These are set on objects by the higher-level storage systems that use the OSD for persistent storage. For example, attributes might be used to classify objects, or to capture relationships among different objects stored on different OSDs.

 

A list command returns a list of identifiers for objects within a partition, optionally filtered by matches against their attribute values. A list command can also return selected attributes of the listed objects.

 

Read and write commands can be combined, or piggy-backed, with commands to get and set attributes. This ability reduces the number of times a high-level storage system has to cross the interface to the OSD, which can improve overall efficiency.

 

#### OSD version 2

 

A second generation of the SCSI command set, "Object-Based Storage Devices - 2" (OSD-2) added support for snapshots, collections of objects, and improved error handling.[[40]](./Object_storage#cite_note-40)

 

A [snapshot](./Snapshot_(computer_storage)) is a point-in-time copy of all the objects in a partition into a new partition. The OSD can implement a space-efficient copy using [copy-on-write](./Copy-on-write) techniques so that the two partitions share objects that are unchanged between the snapshots, or the OSD might physically copy the data to the new partition. The standard defines clones, which are writeable, and snapshots, which are read-only.

 

A collection is a special kind of object that contains the identifiers of other objects. There are operations to add and delete from collections, and there are operations to get or set attributes for all the objects in a collection. Collections are also used for error reporting.  If an object becomes damaged by the occurrence of a media defect (i.e., a bad spot on the disk) or by a software error within the OSD implementation, its identifier is put into a special error collection. The higher-level storage system that uses the OSD can query this collection and take corrective action as necessary.

 

## Differences between key–value and object stores

 

The border between an object store and a [key–value store](./Key–value_store) is blurred, with key–value stores being sometimes loosely referred to as object stores.

 

A traditional block storage interface uses a series of fixed size blocks which are numbered starting at 0. Data must be that exact fixed size and can be stored in a particular block which is identified by its logical block number (LBN). Later, one can retrieve that block of data by specifying its unique LBN.

 

With a key–value store, data is identified by a key rather than a LBN. A key might be "cat" or "olive" or "42". It can be an arbitrary sequence of bytes of arbitrary length. Data (called a value in this parlance) does not need to be a fixed size and also can be an arbitrary sequence of bytes of arbitrary length. One stores data by presenting the key and data (value) to the data store and can later retrieve the data by presenting the key. This concept is seen in programming languages. Python calls them dictionaries, Perl calls them hashes, Java, Rust and C++ call them maps, etc. Several data stores also implement key–value stores such as Memcached, Redis and CouchDB.

 

Object stores are similar to key–value stores in two respects. First, the object identifier or [URL](./URL) (the equivalent of the key) can be an arbitrary string.[[41]](./Object_storage#cite_note-41) Second, data may be of an arbitrary size.

 

There are, however, a few key differences between key–value stores and object stores. First, object stores also allow one to associate a limited set of attributes (metadata) with each piece of data. The combination of a key, value, and set of attributes is referred to as an object. Second, object stores are optimized for large amounts of data (hundreds of megabytes or even gigabytes), whereas for key–value stores the value is expected to be relatively small (kilobytes). Finally, object stores usually offer weaker consistency guarantees such as [eventual consistency](./Eventual_consistency), whereas key–value stores offer [strong consistency](./Strong_consistency).

 

## See also

 
- [Block storage](./Block_storage)
- [File storage](./File_storage)
- [Cloud storage](./Cloud_storage)
- [Clustered file system](./Clustered_file_system)
- [Object access method](./Object_access_method)

 

## References

 
1. [↑](./Object_storage#cite_ref-1) Mesnier, M.; Ganger, G.R.; Riedel, E. (August 2003). "Storage area networking - Object-based storage". *[IEEE Communications Magazine](./IEEE_Communications_Magazine)*. **41** (8): 84–90. [doi](./Doi_(identifier)):[10.1109/mcom.2003.1222722](https://doi.org/10.1109%2Fmcom.2003.1222722).
2. [↑](./Object_storage#cite_ref-2) Porter De Leon, Yadin; Tony Piscopo (14 August 2014). ["Object Storage versus Block Storage: Understanding the Technology Differences"](http://www.druva.com/blog/object-storage-versus-block-storage-understanding-technology-differences/). [Druva](./Druva). [Archived](https://web.archive.org/web/20220123004158/https://www.druva.com/blog/object-storage-versus-block-storage-understanding-technology-differences/) from the original on 23 January 2022. Retrieved 19 January 2015.
3. [1](./Object_storage#cite_ref-objectstorage_3-0) [2](./Object_storage#cite_ref-objectstorage_3-1) Erwin, Derek (2022). ["Block Storage vs. Object Storage vs. File Storage: What's the Difference?"](https://qumulo.com/blog/block-storage-vs-object-storage-vs-file-storage/). [Qumulo](./Qumulo). [Archived](https://web.archive.org/web/20220208221433/https://qumulo.com/jhvhjvblog/block-storage-vs-object-storage-vs-file-storage/) from the original on 8 February 2022. Retrieved 8 February 2022. Object storage can work well for unstructured data in which data is written once and read once (or many times). Static online content, data backups, image archives, videos, pictures, and music files can be stored as objects.
4. [↑](./Object_storage#cite_ref-4) Chandrasekaran, Arun; Dayley, Alan (11 February 2014). ["Critical Capabilities for Object Storage"](https://web.archive.org/web/20140316005328/http://www.gartner.com/technology/reprints.do?id=1-1R78PJ9&ct=140226&st=sb). *[Gartner Research](./Gartner_Research)*. Archived from [the original](http://www.gartner.com/technology/reprints.do?id=1-1R78PJ9&ct=140226&st=sb) on 2014-03-16.
5. [↑](./Object_storage#cite_ref-true-story_5-0) Starkey, James (1997-01-22). ["The true story of BLOBs"](https://www.ibphoenix.com/resources/documents/history/doc_299). [Archived](https://web.archive.org/web/20231108173312/https://www.ibphoenix.com/resources/documents/history/doc_299) from the original on 2023-11-08. Retrieved 2023-11-08.
6. [↑](./Object_storage#cite_ref-NASD_6-0) Garth A. Gibson; Nagle D.; Amiri K.; Chan F.; Feinberg E.; Gobioff H.; Lee C.; Ozceri B.; Riedel E.; Rochberg D.; Zelenka J. ["File Server Scaling with Network-Attached Secure Disks"](http://www.pdl.cmu.edu/ftp/NASD/Sigmetrics97.pdf) (PDF). Proceedings of the ACM International Conference on Measurement and Modeling of Computer Systems (Sigmetrics '97). [Archived](https://web.archive.org/web/20220120114111/https://www.pdl.cmu.edu/ftp/NASD/Sigmetrics97.pdf) (PDF) from the original on 20 January 2022. Retrieved 27 October 2013.
7. [↑](./Object_storage#cite_ref-7) Factor, Michael; Meth, K.; Naor, D.; Rodeh, O.; Satran, J. (2005). "Object Storage: The Future Building Block for Storage Systems". pp. 119–123. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.122.3959](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.122.3959).
8. [↑](./Object_storage#cite_ref-8) Gobioff, Howard; Gibson, Garth A.; Tygar, Doug (1 October 1997). ["Security for Network Attached Storage Devices (CMU-CS-97-185)"](http://repository.cmu.edu/cgi/viewcontent.cgi?article=1147&context=pdl). Parallel Data Laboratory. [Archived](https://web.archive.org/web/20160304032709/http://repository.cmu.edu/cgi/viewcontent.cgi?article=1147&context=pdl) from the original on 4 March 2016. Retrieved 7 November 2013.
9. [↑](./Object_storage#cite_ref-9) Sanjay Ghemawat; Howard Gobioff; Shun-Tak Leung (October 2003). ["The Google File System"](http://research.google.com/archive/gfs-sosp2003.pdf) (PDF). [Archived](https://web.archive.org/web/20091214232923/http://research.google.com/archive/gfs-sosp2003.pdf) (PDF) from the original on 14 December 2009. Retrieved 7 November 2013.
10. [↑](./Object_storage#cite_ref-Lustre_10-0) Braam, Peter. ["Lustre: The intergalactic file system"](https://web.archive.org/web/20171201182053/https://ols.fedoraproject.org/OLS/Reprints-2002/braam-reprint.pdf) (PDF). Archived from [the original](https://ols.fedoraproject.org/OLS/Reprints-2002/braam-reprint.pdf) (PDF) on 1 December 2017. Retrieved 17 September 2013.
11. [↑](./Object_storage#cite_ref-11) ["OceanStore"](https://web.archive.org/web/20120808163557/http://oceanstore.cs.berkeley.edu/). Archived from [the original](http://oceanstore.cs.berkeley.edu/) on 8 August 2012. Retrieved 18 September 2013.
12. [↑](./Object_storage#cite_ref-12) Kubiatowicz, John; Wells, Chris; Zhao, Ben; Bindel, David; Chen, Yan; Czerwinski, Steven; Eaton, Patrick; Geels, Dennis; Gummadi, Ramakrishna; Rhea, Sean; Weatherspoon, Hakim (2000). "OceanStore: An architecture for global-scale persistent storage". *Proceedings of the ninth international conference on Architectural support for programming languages and operating systems*. pp. 190–201. [doi](./Doi_(identifier)):[10.1145/378993.379239](https://doi.org/10.1145%2F378993.379239). [ISBN](./ISBN_(identifier)) [1581133170](./Special:BookSources/1581133170).
13. [↑](./Object_storage#cite_ref-13) Plank, James; Beck, Micah; Elwasif, Wael; Moore, Terry; Swany, Martin; Wolski, Rich (October 1999). ["The Internet Backplane Protocol: Storage in the Network"](http://web.eecs.utk.edu/~jplank/plank/papers/NS99-IBP.pdf) (PDF). *Netstore 1999*. [Archived](https://web.archive.org/web/20220621101357/http://web.eecs.utk.edu/~jplank/plank/papers/NS99-IBP.pdf) (PDF) from the original on 21 June 2022. Retrieved 27 January 2021.
14. [↑](./Object_storage#cite_ref-14) *Object Storage: What, How and Why?*, NSF (Networking Storage Forum), SNIA (Storage Networking Industry Association), Live [Webcast](https://www.snia.org/sites/default/files/ESF/Object-Sorage-What-How-Why-Final.pdf) [Archived](https://web.archive.org/web/20220812142124/https://www.snia.org/sites/default/files/ESF/Object-Sorage-What-How-Why-Final.pdf) 2022-08-12 at the [Wayback Machine](./Wayback_Machine) February 19, 2020
15. [↑](./Object_storage#cite_ref-15) Anderson, D. (1999). ["Object based storage devices: a command set proposal"](https://www.t10.org/ftp/t10/document.99/99-315r0.pdf) (PDF). *T10*. [S2CID](./S2CID_(identifier)) [59781155](https://api.semanticscholar.org/CorpusID:59781155). [Archived](https://web.archive.org/web/20220121225613/https://www.t10.org/ftp/t10/document.99/99-315r0.pdf) (PDF) from the original on 2022-01-21. Retrieved 2021-10-23.
16. [↑](./Object_storage#cite_ref-16) *Object Based Storage: A Vision*, slide presentation, Dave Anderson and Seagate Technology, October 13, 1999 [https://www.t10.org/ftp/t10/document.99/99-341r0.pdf](https://www.t10.org/ftp/t10/document.99/99-341r0.pdf) [Archived](https://web.archive.org/web/20220811092815/https://www.t10.org/ftp/t10/document.99/99-341r0.pdf) 2022-08-11 at the [Wayback Machine](./Wayback_Machine)
17. [↑](./Object_storage#cite_ref-pritchard1_17-0) Pritchard, Stephen (23 October 2020). ["Unified file and object storage: The best of both worlds?"](https://www.computerweekly.com/feature/Unified-file-and-object-storage-The-best-of-both-worlds). *Computer Weekly*. [Archived](https://web.archive.org/web/20220625142034/https://www.computerweekly.com/feature/Unified-file-and-object-storage-The-best-of-both-worlds) from the original on 25 June 2022. Retrieved 21 June 2022.
18. [1](./Object_storage#cite_ref-haystack_18-0) [2](./Object_storage#cite_ref-haystack_18-1) Vajgel, Peter (30 April 2009). ["Needle in a haystack: efficient storage of billions of photos"](https://engineering.fb.com/2009/04/30/core-data/needle-in-a-haystack-efficient-storage-of-billions-of-photos/). [Archived](https://web.archive.org/web/20211005140617/https://engineering.fb.com/2009/04/30/core-data/needle-in-a-haystack-efficient-storage-of-billions-of-photos/) from the original on 5 October 2021. Retrieved 5 October 2021.
19. [↑](./Object_storage#cite_ref-19) Riedel, Erik; Sami Iren (February 2007). ["Object Storage and Applications"](https://www.usenix.org/legacy/event/lsf07/tech/riedel.pdf) (PDF). [Archived](https://web.archive.org/web/20220811092816/https://www.usenix.org/legacy/event/lsf07/tech/riedel.pdf) (PDF) from the original on 11 August 2022. Retrieved 3 November 2013.
20. [↑](./Object_storage#cite_ref-20) ["The Seagate Kinetic Open Storage Vision"](http://www.seagate.com/tech-insights/kinetic-vision-how-seagate-new-developer-tools-meets-the-needs-of-cloud-storage-platforms-master-ti/). Seagate. [Archived](https://web.archive.org/web/20190616183941/https://www.seagate.com/tech-insights/kinetic-vision-how-seagate-new-developer-tools-meets-the-needs-of-cloud-storage-platforms-master-ti/) from the original on 16 June 2019. Retrieved 3 November 2013.
21. [↑](./Object_storage#cite_ref-21) Gallagher, Sean (27 October 2013). ["Seagate introduces a new drive interface: Ethernet"](https://arstechnica.com/information-technology/2013/10/seagate-introduces-a-new-drive-interface-ethernet/). [Ars Technica](./Ars_Technica). [Archived](https://web.archive.org/web/20220621101355/https://arstechnica.com/information-technology/2013/10/seagate-introduces-a-new-drive-interface-ethernet/) from the original on 21 June 2022. Retrieved 3 November 2013.
22. [↑](./Object_storage#cite_ref-22) Corbet, Jonathan (4 November 2008). ["Linux and object storage devices"](https://lwn.net/Articles/305740/). *LWN.net*. [Archived](https://web.archive.org/web/20220320175150/http://lwn.net/Articles/305740/) from the original on 20 March 2022. Retrieved 8 November 2013.
23. [↑](./Object_storage#cite_ref-23) Dilger, Andreas. ["Lustre Future Development"](https://web.archive.org/web/20131029195656/http://storageconference.org/2012/Presentations/M04.Dilger.pdf) (PDF). IEEE MSST. Archived from [the original](http://storageconference.org/2012/Presentations/M04.Dilger.pdf) (PDF) on 29 October 2013. Retrieved 27 October 2013.
24. [↑](./Object_storage#cite_ref-24) ["Datadirect Networks to build world's fastest storage system for Titan, the world's most powerful supercomputer"](https://web.archive.org/web/20131029194043/http://www.multivu.com/mnr/60497-datadirect-networks-titan-supercomputer-storage-system-ornl). Archived from [the original](http://www.multivu.com/mnr/60497-datadirect-networks-titan-supercomputer-storage-system-ornl) on 29 October 2013. Retrieved 27 October 2013.
25. [↑](./Object_storage#cite_ref-25) ["EMC Marks Five Years of EMC Centera Innovation and Market Leadership"](http://www.emc.com/about/news/press/us/2007/04182007-5028.htm). EMC. 18 April 2007. [Archived](https://web.archive.org/web/20140123191050/http://www.emc.com/about/news/press/us/2007/04182007-5028.htm) from the original on 23 January 2014. Retrieved 3 November 2013.
26. [↑](./Object_storage#cite_ref-26) ["Hitachi Content Platform Supports Multiple Petabytes, Billions of Objects"](https://web.archive.org/web/20150924113750/http://www.techvalidate.com/portals/hitachi-content-platform-customers-with-more-than-1pb-of-data-stored). Techvalidate.com. Archived from [the original](http://www.techvalidate.com/portals/hitachi-content-platform-customers-with-more-than-1pb-of-data-stored) on 24 September 2015. Retrieved 19 September 2013.
27. [↑](./Object_storage#cite_ref-27) Robb, Drew (11 May 2011). ["EMC World Continues Focus on Big Data, Cloud and Flash"](https://www.infostor.com/backup-and_recovery/cloud-storage/emc-world-continues-focus-on-big-data-cloud-and-flash-.html). *Infostor*. [Archived](https://web.archive.org/web/20211207192045/https://www.infostor.com/backup-and_recovery/cloud-storage/emc-world-continues-focus-on-big-data-cloud-and-flash-.html) from the original on 7 December 2021. Retrieved 19 September 2013.
28. [↑](./Object_storage#cite_ref-28) Hamilton, George. ["In it for the Long Run: EMC's Object Storage Leadership"](https://web.archive.org/web/20140315172511/http://www.rethinkstorage.com/in-it-for-the-long-run-emcs-object-storage-leadership#.UyEzj9yllFI). Archived from [the original](http://www.rethinkstorage.com/in-it-for-the-long-run-emcs-object-storage-leadership#.UyEzj9yllFI) on 15 March 2014. Retrieved 15 March 2014.
29. [↑](./Object_storage#cite_ref-29) Mellor, Chris (1 July 2014). ["Los Alamos National Laboratory likes it, puts Scality's RING on it"](https://www.theregister.co.uk/2014/07/01/scalitys_ring_goes_faster/). [The Register](./The_Register). [Archived](https://web.archive.org/web/20200107003408/https://www.theregister.co.uk/2014/07/01/scalitys_ring_goes_faster/) from the original on 7 January 2020. Retrieved 26 January 2015.
30. [↑](./Object_storage#cite_ref-30) Miller, Rich (13 January 2013). ["Facebook Builds Exabyte Data Centers for Cold Storage"](http://www.datacenterknowledge.com/archives/2013/01/18/facebook-builds-new-data-centers-for-cold-storage/). *Datacenterknowledge.com*. [Archived](https://web.archive.org/web/20140522004410/http://www.datacenterknowledge.com/archives/2013/01/18/facebook-builds-new-data-centers-for-cold-storage/) from the original on 22 May 2014. Retrieved 6 November 2013.
31. [↑](./Object_storage#cite_ref-31) Leung, Leo (17 May 2014). ["How much data does x store?"](https://web.archive.org/web/20140522002448/http://techexpectations.org/2014/05/17/how-much-data-does-x-store/). Techexpectations.org. Archived from [the original](http://techexpectations.org/2014/05/17/how-much-data-does-x-store/) on 22 May 2014. Retrieved 23 May 2014.
32. [↑](./Object_storage#cite_ref-32) Leung, Leo (January 11, 2012). ["Object storage already dominates our days (we just didn't notice)"](https://web.archive.org/web/20130929210049/http://blog.oxygencloud.com/2012/01/11/object-storage-already-dominates/). *Oxygen Cloud Blog*. Archived from [the original](http://blog.oxygencloud.com/2012/01/11/object-storage-already-dominates/) on 29 September 2013. Retrieved 27 October 2013.
33. [↑](./Object_storage#cite_ref-33) Harris, Derrick (18 April 2013). ["Amazon S3 goes exponential, now stores 2 trillion objects"](https://web.archive.org/web/20130420042320/http://gigaom.com/2013/04/18/amazon-s3-goes-exponential-now-stores-2-trillion-objects/). [Gigaom](./Gigaom). Archived from [the original](http://gigaom.com/2013/04/18/amazon-s3-goes-exponential-now-stores-2-trillion-objects/) on April 20, 2013. Retrieved 17 September 2013.
34. [↑](./Object_storage#cite_ref-34) Wilhelm, Alex (27 June 2013). ["Microsoft: Azure powers 299M Skype users, 50M Office Web Apps users, stores 8.5T objects"](https://thenextweb.com/microsoft/2013/06/27/microsoft-our-cloud-powers-hundreds-of-millions/). [thenextweb.com](./Thenextweb.com). [Archived](https://web.archive.org/web/20210226130909/https://thenextweb.com/microsoft/2013/06/27/microsoft-our-cloud-powers-hundreds-of-millions/) from the original on 26 February 2021. Retrieved 18 September 2013.
35. [↑](./Object_storage#cite_ref-35) Nelson, Fritz (4 April 2014). ["Microsoft Azure's 44 New Enhancements, 20 Trillion Objects"](https://web.archive.org/web/20140506205143/http://www.tomsitpro.com/articles/microsoft-azure-paas-iaas-cloud-computing,1-1841.html). Tom's IT Pro. Archived from [the original](http://www.tomsitpro.com/articles/microsoft-azure-paas-iaas-cloud-computing,1-1841.html) on 6 May 2014. Retrieved 3 September 2014.
36. [↑](./Object_storage#cite_ref-36) Calder, Brad. ["Windows Azure Storage: A Highly Available Cloud Storage Service with Strong Consistency"](http://sigops.org/sosp/sosp11/current/2011-Cascais/printable/11-calder.pdf) (PDF). *SOSP '11: Proceedings of the Twenty-third ACM SIGOPS Symposium on Operating Systems Principles*. Association for Computing Machinery. [ISBN](./ISBN_(identifier)) [978-1-4503-0977-6](./Special:BookSources/978-1-4503-0977-6). [Archived](https://web.archive.org/web/20171013074027/http://sigops.org/sosp/sosp11/current/2011-Cascais/printable/11-calder.pdf) (PDF) from the original on 13 October 2017. Retrieved 6 November 2013.
37. [↑](./Object_storage#cite_ref-37) Nicolas, Philippe (2024-12-18). ["Coldago Map 2024 for Object Storage"](https://www.storagenewsletter.com/2024/12/18/coldago-map-2024-for-object-storage/). *StorageNewsletter*. Retrieved 2025-07-22.
38. [↑](./Object_storage#cite_ref-38) ["Map 2024 for Object Storage"](https://www.coldago.net/mapobj). *Coldago Research*. Retrieved 2025-07-22.
39. [↑](./Object_storage#cite_ref-39) ["INCITS 400-2004"](https://store.accuristech.com/ieee/standards/incits-400-2004?product_id=1204555). [InterNational Committee for Information Technology Standards](./InterNational_Committee_for_Information_Technology_Standards). [Archived](https://web.archive.org/web/20240422155758/https://store.accuristech.com/ieee/standards/incits-400-2004?product_id=1204555) from the original on 22 April 2024. Retrieved 8 November 2013.
40. [↑](./Object_storage#cite_ref-40) ["INCITS 458-2011"](https://store.accuristech.com/ieee/standards/incits-458-2011?product_id=1801667). InterNational Committee for Information Technology Standards. 15 March 2011. [Archived](https://web.archive.org/web/20240422155759/https://store.accuristech.com/ieee/standards/incits-458-2011?product_id=1801667) from the original on 22 April 2024. Retrieved 8 November 2013.
41. [↑](./Object_storage#cite_ref-41) [OpenStack Foundation](./OpenStack_Foundation). ["Object Storage API overview"](https://docs.openstack.org/developer/swift/api/object_api_v1_overview.html). *OpenStack Documentation*. [Archived](https://web.archive.org/web/20170703024655/https://docs.openstack.org/developer/swift/api/object_api_v1_overview.html) from the original on 3 July 2017. Retrieved 9 June 2017.

 
| vteData storage |
| --- |
| Fundamental storage technologies | Semiconductor memoryMagnetic storageOptical storagePaper data storageUncommon storage technologies |
| Related technologies | RoboticsFile systemsData compressionEncryptionRAID |
| Network storage | Networked storageFile serverNetwork-attached storageStorage area network |
| vteMagnetic storagemediaWire(1898)Tape(1928)Drum(1932)Ferrite core(1949)Hard disk(1956)Stripe card(1956)MICR(1956)Thin film(1962)CRAM(1962)Twistor(~1968)Floppy disk(1969)Bubble(~1970)MRAM(1995)Racetrack(2008)vteOptical storagemediaBlu-ray(2006)BD-R(2006)BD-RE(2006)BD-R XL(2010)BD-RE XL(2010)Professional Disc(2003)PDD(2004)DVD(1995)DVD-R(1997)DVD-RW(1999)DVD+RW(2001)DVD+R(2002)DVD+R DL(2004)DVD-R DL(2005)Compact disc(1982)CD-R(1988)CD-i(1991)CD-RW(1997)DiscontinuedMicroform(1870)Optical tape(20th century)Optical disc(20th century)LaserDisc(1978)WORM(1979)GD-ROM(1997)MIL-CD(1999)DataPlay(2002)UDO(2003)ProData(2003)UMD(2004)HD DVD(2006)Magneto-optic Kerr effect(1877)MO disc(1980s)MiniDisc(1992)MD Data(1993)Hi-MD(2004)Optical AssistLaser turntable(1986)Floptical(1991)Super DLT(1998)vtePaper data storagemediaAntiquityWritingonpapyrus(c. 3000 BCE)Paper(105 CE)ModernIndex card(1640s)Punched tape(mid-1800s)Punched card(1880s)Edge-notched card(1904)Optical mark recognition(1930s)Barcode(1948) | vteMagnetic storagemedia | Wire(1898)Tape(1928)Drum(1932)Ferrite core(1949)Hard disk(1956)Stripe card(1956)MICR(1956)Thin film(1962)CRAM(1962)Twistor(~1968)Floppy disk(1969)Bubble(~1970)MRAM(1995)Racetrack(2008) | vteOptical storagemedia | Blu-ray(2006) | BD-R(2006)BD-RE(2006)BD-R XL(2010)BD-RE XL(2010) | Professional Disc(2003) | PDD(2004) | DVD(1995) | DVD-R(1997)DVD-RW(1999)DVD+RW(2001)DVD+R(2002)DVD+R DL(2004)DVD-R DL(2005) | Compact disc(1982) | CD-R(1988)CD-i(1991)CD-RW(1997) | Discontinued | Microform(1870)Optical tape(20th century)Optical disc(20th century)LaserDisc(1978)WORM(1979)GD-ROM(1997)MIL-CD(1999)DataPlay(2002)UDO(2003)ProData(2003)UMD(2004)HD DVD(2006) | Magneto-optic Kerr effect(1877) | MO disc(1980s)MiniDisc(1992)MD Data(1993)Hi-MD(2004) | Optical Assist | Laser turntable(1986)Floptical(1991)Super DLT(1998) | vtePaper data storagemedia | Antiquity | Writingonpapyrus(c. 3000 BCE)Paper(105 CE) | Modern | Index card(1640s)Punched tape(mid-1800s)Punched card(1880s)Edge-notched card(1904)Optical mark recognition(1930s)Barcode(1948) |
| vteMagnetic storagemedia |
| Wire(1898)Tape(1928)Drum(1932)Ferrite core(1949)Hard disk(1956)Stripe card(1956)MICR(1956)Thin film(1962)CRAM(1962)Twistor(~1968)Floppy disk(1969)Bubble(~1970)MRAM(1995)Racetrack(2008) |
| vteOptical storagemedia |
| Blu-ray(2006) | BD-R(2006)BD-RE(2006)BD-R XL(2010)BD-RE XL(2010) |
| Professional Disc(2003) | PDD(2004) |
| DVD(1995) | DVD-R(1997)DVD-RW(1999)DVD+RW(2001)DVD+R(2002)DVD+R DL(2004)DVD-R DL(2005) |
| Compact disc(1982) | CD-R(1988)CD-i(1991)CD-RW(1997) |
| Discontinued | Microform(1870)Optical tape(20th century)Optical disc(20th century)LaserDisc(1978)WORM(1979)GD-ROM(1997)MIL-CD(1999)DataPlay(2002)UDO(2003)ProData(2003)UMD(2004)HD DVD(2006) |
| Magneto-optic Kerr effect(1877) | MO disc(1980s)MiniDisc(1992)MD Data(1993)Hi-MD(2004) |
| Optical Assist | Laser turntable(1986)Floptical(1991)Super DLT(1998) |
| vtePaper data storagemedia |
| Antiquity | Writingonpapyrus(c. 3000 BCE)Paper(105 CE) |
| Modern | Index card(1640s)Punched tape(mid-1800s)Punched card(1880s)Edge-notched card(1904)Optical mark recognition(1930s)Barcode(1948) |