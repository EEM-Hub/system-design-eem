---
source: https://en.wikipedia.org/wiki/Append-only
fetched: 2026-06-19
---

Property of computer data storage 

**Append-only** is a property of [computer data storage](./Computer_data_storage) such that new data can be appended to the storage, but where existing data is [immutable](./Immutable).

 

## Access control

 

Many [file systems'](./File_system) [Access Control Lists](./Access-control_list) implement an "append-only" permission:

 
- [chattr](./Chattr) in Linux can be used to set the append-only flag to files and directories. This corresponds to the `O_APPEND` flag in [`open()`](./Open_(system_call)).[[1]](./Append-only#cite_note-1)
- [NTFS](./NTFS) ACL has a control for "Create Folders / Append Data", but it does not seem to keep data immutable.[[2]](./Append-only#cite_note-2)

 

Many [cloud storage](./Cloud_storage) providers provide the ability to limit access as append-only.[[3]](./Append-only#cite_note-3) This feature is especially important to mitigate the risk of [data loss](./Data_loss) for [backup](./Backup) policies in the event that the computer being backed-up becomes infected with [ransomware](./Ransomware) capable of deleting or encrypting the computer's backups.[[4]](./Append-only#cite_note-4)[[5]](./Append-only#cite_note-5)

 

## Data structures

 

Many [data structures](./Data_structures) and [databases](./Databases) implement [immutable objects](./Immutable_objects), effectively making their data structures append-only. Implementing an append-only data structure has many benefits, such as ensuring data [consistency](./Consistency_(database_systems)), improving [performance](./Computer_performance),[[6]](./Append-only#cite_note-dbsmr-6) and permitting [rollbacks](./Rollback_(data_management)).[[7]](./Append-only#cite_note-redis-7)[[8]](./Append-only#cite_note-8)

 

The prototypical append-only data structure is the [log file](./Log_file). Log-structured data structures found in [Log-structured file systems](./Log-structured_file_system) and databases work in a similar way: every change (transaction) that happens to the data is logged by the program, and on retrieval the program must combine the pieces of data found in this log file.[[9]](./Append-only#cite_note-flash-9) [Blockchains](./Blockchain) add [cryptography](./Cryptography) to the logs so that every transaction is verifiable.

 

Append-only data structures may also be mandated by the hardware or software environment:

 
- All objects are immutable in [purely functional programming](./Purely_functional_programming) languages, where every function is pure and global states do not exist.[[10]](./Append-only#cite_note-10)
- [Flash storage](./Flash_storage) cells can only be written to once before erasing. Erasing on a flash drive works on the level of pages which cover many cells at once, so each page is treated as an append-only set of cells until it fills up.[[9]](./Append-only#cite_note-flash-9)[[11]](./Append-only#cite_note-11)
- Hard drives that use [shingled magnetic recording](./Shingled_magnetic_recording) cannot be written to randomly because writing on a track would clobber a neighboring, usually later, track. As a result, each "zone" on the drive is append-only.[[12]](./Append-only#cite_note-12)[[6]](./Append-only#cite_note-dbsmr-6)

 

Append-only data structures grow over time, with more and more space dedicated to "stale" data found only in the history and more time wasted on parsing these data. A number of append-only systems implement *rewriting* (copying [garbage collection](./Garbage_collection_(computer_science))), so that a new structure is created only containing the current version and optionally a few older ones.[[7]](./Append-only#cite_note-redis-7)[[13]](./Append-only#cite_note-fast16-13)

 

## See also

 
- [Access control list](./Access_control_list)
- [Cloud storage](./Cloud_storage)
- [Comparison of file hosting services](./Comparison_of_file_hosting_services)
- [Data structure](./Data_structure)
- [Purely functional data structure](./Purely_functional_data_structure)
- [Log-structured merge-tree](./Log-structured_merge-tree)
- [Certificate Transparency](./Certificate_Transparency)
- [Write once read many](./Write_once_read_many)

 

## References

  
1. [↑](./Append-only#cite_ref-1) `chattr(1)` – [Linux](./Linux) User [Manual](./Man_page) – User Commands
2. [↑](./Append-only#cite_ref-2) ["powershell - How to give "only append" access to user in windows , for logging purposes"](https://serverfault.com/a/476952). *Server Fault*.
3. [↑](./Append-only#cite_ref-3) Jim Donovan (September 11, 2018). ["Why Use Immutable Storage?"](https://wasabi.com/blog/use-immutable-storage/). *Wasabi*.
4. [↑](./Append-only#cite_ref-4) Eugene Kolodenker; William Koch; Gianluca Stringhini; Manuel Egele (April 2017). "PayBreak: Defense Against Cryptographic Ransomware". *Proceedings of the 2017 ACM on Asia Conference on Computer and Communications Security*. pp. 599–611. [doi](./Doi_(identifier)):[10.1145/3052973.3053035](https://doi.org/10.1145%2F3052973.3053035). Due to the threat of ransomware targeting the key vault, our implementation stores the harvested key material into an append-only file protected with Administrator privileges.
5. [↑](./Append-only#cite_ref-5) Pont, Jamie; Abu Oun, Osama; Brierley, Calvin; Arief, Budi; Hernandez-Castro, Julio (2019). "A Roadmap for Improving the Impact of Anti-ransomware Research". [*Secure IT Systems, Proceedings of 24th Nordic Conference, NordSec 2019*](https://www.researchgate.net/publication/337215603). Springer International Publishing. pp. 137–154. [ISBN](./ISBN_(identifier)) [978-3-030-35055-0](./Special:BookSources/978-3-030-35055-0).
6. [1](./Append-only#cite_ref-dbsmr_6-0) [2](./Append-only#cite_ref-dbsmr_6-1) Magic Pocket Hardware Engineering Teams. ["Extending Magic Pocket Innovation with the first petabyte scale SMR drive deployment"](https://dropbox.tech/infrastructure/extending-magic-pocket-innovation-with-the-first-petabyte-scale-smr-drive-deployment). *dropbox.tech*.
7. [1](./Append-only#cite_ref-redis_7-0) [2](./Append-only#cite_ref-redis_7-1) ["Redis Persistence"](https://redis.io/topics/persistence). *Redis*.
8. [↑](./Append-only#cite_ref-8) ["Additional Notes"](https://borgbackup.readthedocs.io/en/stable/usage/notes.html#append-only-mode). *Borg Deduplicating Archiver 1.1.11 documentation*.
9. [1](./Append-only#cite_ref-flash_9-0) [2](./Append-only#cite_ref-flash_9-1) Reid, Colin; Bernstein, Phil (1 January 2010). ["Implementing an Append-Only Interface for Semiconductor Storage"](http://sites.computer.org/debull/A10dec/hyder.pdf) (PDF). *IEEE Data Eng. Bull*. **33**: 14–20.
10. [↑](./Append-only#cite_ref-10) ["Thirteen ways of looking at a turtle"](https://fsharpforfunandprofit.com/posts/13-ways-of-looking-at-a-turtle/#2-basic-fp---a-module-of-functions-with-immutable-state). *F# for fun and profit*. Retrieved 2018-11-13.
11. [↑](./Append-only#cite_ref-11) ["NVMe Zoned Namespace"](https://web.archive.org/web/20200129163241/https://zonedstorage.io/introduction/zns/). *ZonedStorage.io*. Archived from [the original](https://zonedstorage.io/introduction/zns/) on 2020-01-29. Retrieved 2020-04-25. The internals of Solid State Drives are such that they implement a log-structured data structure, where data is written sequentially to the media.
12. [↑](./Append-only#cite_ref-12) Jake Edge (March 26, 2014). ["Support for shingled magnetic recording devices"](https://lwn.net/Articles/591782/). [LWN.net](./LWN.net). Retrieved December 14, 2014.
13. [↑](./Append-only#cite_ref-fast16_13-0) Brewer, Eric; Ying, Lawrence; Greenfield, Lawrence; Cypher, Robert; T'so, Theodore (2016). ["Disks for Data Centers"](https://research.google/pubs/pub44830/). *Proceedings of USENIX FAST 2016*. Because of the write restrictions imposed by SMR, when data is deleted, that deleted capacity can not be reused until the system copies the remaining live data in that SMR zone to another part of the disk, a form of garbage collection (GC).