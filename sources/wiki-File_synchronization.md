---
source: https://en.wikipedia.org/wiki/File_synchronization
fetched: 2026-06-19
---

Mirroring of computer files
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"File synchronization"–news·newspapers·books·scholar·JSTOR(February 2019)(Learn how and when to remove this message) |
| --- | --- |

 

**File synchronization** (or **syncing**) in computing is the process of ensuring that [computer files](./Computer_file) in two or more locations are updated via certain rules.

 

In *one-way file synchronization*, also called [mirroring](./Web_mirror), updated files are copied from a source location to one or more target locations, but no files are copied back to the source location. In *two-way file synchronization*, updated files are copied in both directions, usually with the purpose of keeping the two locations identical to each other. In this article, the term synchronization refers exclusively to two-way file synchronization.

 

[File](./File_system) synchronization is commonly used for home backups on external hard drives or updating for transport on [USB flash drives](./USB_flash_drives). [BitTorrent Sync](./BitTorrent_Sync), [Dropbox](./Dropbox_(service)), [SKYSITE](./Skysite), [Nextcloud](./Nextcloud), [OneDrive](./OneDrive), [Google Drive](./Google_Drive) and [iCloud](./ICloud) are prominent products. Some [backup software](./Backup_software) also supports real-time file sync. The automatic process prevents copying already identical files and thus can be faster and save much time versus a manual copy, and is less error prone.[[1]](./File_synchronization#cite_note-1) However this suffers from the limit that the synchronized files must physically fit in the portable storage device. Synchronization software that only keeps a list of files and the changed files eliminates this problem (e.g. the "snapshot" feature in [Beyond Compare](./Beyond_Compare) or the "package" feature in [Synchronize It!](./Synchronize_It)). It is especially useful for mobile workers, or others that work on multiple computers.

 

It is possible to synchronize multiple locations by synchronizing them one pair at a time. The [Unison](./Unison_(software)) Manual[[2]](./File_synchronization#cite_note-2) describes how to do this:

 If you need to do this, the most reliable way to set things up is to organize the machines into a "star topology," with one machine designated as the "hub" and the rest as "spokes," and with each spoke machine synchronizing only with the hub. The big advantage of the star topology is that it eliminates the possibility of confusing "spurious conflicts" arising from the fact that a separate archive is maintained by [Unison](./Unison_(software)) for every pair of hosts that it synchronizes. 

## Common features

 

Common features of file synchronization systems include:[*[citation needed](./Wikipedia:Citation_needed)*]

 
- [Encryption](./Encryption) for [security](./Internet_security), especially when synchronizing across the [Internet](./Internet).
- [Compressing](./Data_compression) any data sent across a network.
- *Conflict detection* where a file has been modified on both sources, as opposed to where it has only been modified on one. Undetected conflicts can lead to overwriting copies of the file with the most recent version, causing data loss. For conflict detection, the synchronization software needs to keep a database of the synchronized files. Distributed conflict detection can be achieved by [version vectors](./Version_vector).
- *Open Files Support* ensures data integrity when copying data or application files that are in-use or database files that are exclusively [locked](./File_locking).
- Specific support for using an intermediate storage device, such as a removable flash disc, to synchronize two machines. Most synchronizing programs can be used in this way, but providing specific support for this can reduce the amount of data stored on a device.
- The ability to preview any changes before they are made.
- The ability to view differences in individual files.
- Backup between operating systems and transfer between network computers.[[3]](./File_synchronization#cite_note-3)
- Ability to edit or use files on multiple computers or operating systems.

 

## Comparison to shared file access

 This section is an excerpt from [Shared resource § Comparison to file synchronization](./Shared_resource#Comparison_to_file_synchronization).[[edit](https://en.wikipedia.org/w/index.php?title=Shared_resource&action=edit)] 

Shared file access involves but should not be confused with file synchronization and other information synchronization. Internet-based information synchronization may, for example, use the [SyncML](./SyncML) language. Shared file access is based on server-side pushing of folder information, and is normally used over an "always on" [Internet socket](./Internet_socket). File synchronization allows the user to be offline from time to time and is normally based on an agent software that polls synchronized machines at reconnect, and sometimes repeatedly with a certain time interval, to discover differences. Modern operating systems often include a local [cache](./Web_cache) of remote files, allowing [offline access](./Offline_access?action=edit&redlink=1) and synchronization when reconnected.

   

## Possible security concerns

 

Consumer-grade file synchronization solutions are popular, however for business use, they create a concern of allowing corporate information to sprawl to unmanaged devices and cloud services which are uncontrolled by the organization.[*[citation needed](./Wikipedia:Citation_needed)*]

 

When using cloud services, data privacy risks can be mitigated by using a file synchronization solution that features [end-to-end encryption](./End-to-end_encryption) instead of simple transport ([HTTPS](./HTTPS)) or at-rest encryption.

 

## See also

 
- [Backup software](./Backup_software)
- [Comparison of file synchronization software](./Comparison_of_file_synchronization_software)
- [Comparison of online backup services](./Comparison_of_online_backup_services)
- [Data comparison](./Data_comparison)
- [Data synchronization](./Data_synchronization)
- [Mirror (computing)](./Web_mirror)
- [Remote backup service](./Remote_backup_service)
- [Shared file access](./Shared_file_access)
- [List of backup software](./List_of_backup_software)

 

## References

  
1. [↑](./File_synchronization#cite_ref-1) [A. Tridgell](./Andrew_Tridgell) (February 1999). ["Efficient algorithms for sorting and synchronization"](https://samba.org/~tridge/phd_thesis.pdf) (PDF). PhD thesis. The Australian National University.
2. [↑](./File_synchronization#cite_ref-2) [Pierce, Benjamin](./Benjamin_C._Pierce) (2009). ["Unison File Synchronizer. User Manual and Reference Guide"](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#usingmultiple). Retrieved 27 January 2014.
3. [↑](./File_synchronization#cite_ref-3) ["Why Should You Backup Your Mac to a Windows (OS based) Computer?"](https://web.archive.org/web/20141202010312/http://www.backupitnow.com/why-should-you-back-up-your-mac-to-a-windows-os-based-computer/). Wei-Soft. Archived from [the original](http://www.backupitnow.com/why-should-you-back-up-your-mac-to-a-windows-os-based-computer/) on 2 December 2014. Retrieved 23 November 2014.

 
| vteComputer files |
| --- |
| Types | Binary file/text fileData fileFile formatList of file formatsList of File signaturesMagic numberOpen file formatsProprietary file formatsMetafileSidecar fileSparse fileSwap fileSystem fileTemporary fileZero-byte file |
| Properties | Filename8.3 filenameLong filenameFilename manglingFilename extensionList of filename extensionsFile attributeExtended file attributesFile sizeHidden file / Hidden directory |
| Organisation | Directory/folderNTFS linksTemporary folderDirectory structureFile systemFilesystem Hierarchy StandardGrid file systemSemantic file systemPath |
| Operations | OpenCloseReadWrite |
| Linking | File descriptorHard linkShortcutAliasShadowSymbolic link |
| Management | BackupFile comparisonFile copyingData compressionFile managerComparison of file managersFile system fragmentationFile-system permissionsFile transferFile sharingFile synchronizationFile verification |