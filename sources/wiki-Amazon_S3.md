---
source: https://en.wikipedia.org/wiki/Amazon_S3
fetched: 2026-06-19
---

Cloud-based object storage service 
|  | The technical content of this article relies largely or entirely on documentation from Amazon.com.Relevant discussion may be found on thetalk page. Please helpimprove this articlebyintroducing  citations to additional sources.Find sources:"Amazon S3"–news·newspapers·books·scholar·JSTOR(November 2018) |
| --- | --- |

 
|  |
| --- |
| Type of site | Cloud storage |
| Availablein | English |
| Owner | Amazon.com |
| URL | aws.amazon.com/s3/ |
| IPv6support | Yes |
| Commercial | Yes |
| Registration | Required (included in free tier layer) |
| Launched | March14, 2006;20 years ago(2006-03-14) |
| Currentstatus | Active |

 

**Amazon Simple Storage Service** (**S3**) is a service offered by [Amazon Web Services](./Amazon_Web_Services) (AWS) that provides [object storage](./Object_storage) through a [web service](./Web_service) interface.[[1]](./Amazon_S3#cite_note-s3_usa-1)[[2]](./Amazon_S3#cite_note-2) Amazon S3 uses the same scalable storage infrastructure that [Amazon.com](./Amazon_(company)) uses to run its e-commerce network.[[3]](./Amazon_S3#cite_note-:1-3) Amazon S3 can store any type of object, which allows uses like storage for Internet applications, backups, disaster recovery, data archives, [data lakes](./Data_lake) for analytics, and [hybrid cloud storage](./Cloud_computing#Hybrid). AWS launched Amazon S3 in the United States on March 14, 2006,[[1]](./Amazon_S3#cite_note-s3_usa-1)[[4]](./Amazon_S3#cite_note-4) then in Europe in November 2007.[[5]](./Amazon_S3#cite_note-s3-europe-5)

  I commented the following out for two reasons. First, the article cited in The Guardian talks about AWS and doesn't separate out which service is the most profitable. Second, the two trillion object information is quite dated and I can't find anything more recent.
Amazon S3 along with [[Amazon Elastic Compute Cloud|EC2]] drive AWS, the most profitable division under the entire Amazon company.<ref name=":0" /&#x3E; Amazon S3 is reported to store more than 2 trillion objects {{as of|2013|04|lc=on}}.<ref name="aws.typepad.com"&#x3E;{{cite web|url=http://aws.typepad.com/aws/2013/04/amazon&#x2D;s3&#x2D;two&#x2D;trillion&#x2D;objects&#x2D;11&#x2D;million&#x2D;requests&#x2D;second.html|title=Amazon S3 – Two Trillion Objects, 1.1 Million Requests / Second &#x2D; Amazon Web Services|date=18 April 2013|website=typepad.com}}</ref&#x3E; 

## Technical details

 

### Design

 

Amazon S3 manages data with an [object storage](./Object_storage) architecture[[6]](./Amazon_S3#cite_note-6) which aims to provide [scalability](./Scalability), [high availability](./High_availability), and [low latency](./Low_latency) with high [durability](./Durability_(database_systems)).[[3]](./Amazon_S3#cite_note-:1-3) The basic storage units of Amazon S3 are objects which are organized into buckets. Each object is identified by a unique, user-assigned key.[[7]](./Amazon_S3#cite_note-7) Buckets can be managed using the console provided by Amazon S3, programmatically with the AWS [SDK](./Software_development_kit), or the [REST](./Representational_State_Transfer) application programming interface. Objects can be up to five [terabytes](./Terabyte) in size.[[8]](./Amazon_S3#cite_note-8)[[9]](./Amazon_S3#cite_note-9) Requests are authorized using an [access control list](./Access_control_list) associated with each object bucket and support [versioning](./Versioning_file_system)[[10]](./Amazon_S3#cite_note-10) which is disabled by default.[[11]](./Amazon_S3#cite_note-11) Amazon S3 can be used to replace static [web-hosting](./Web_hosting_service) infrastructure with HTTP client-accessible objects,[[12]](./Amazon_S3#cite_note-S3_Web_Hosting-12) index document support, and error document support.[[13]](./Amazon_S3#cite_note-13)
The Amazon AWS authentication mechanism allows the creation of authenticated URLs, valid for a specified amount of time. Every item in a bucket can also be served as a [BitTorrent](./BitTorrent_(protocol)) feed. The Amazon S3 store can act as a seed host for a [torrent](./Torrent_file) and any BitTorrent client can retrieve the file. This can drastically reduce the bandwidth cost for the download of popular objects. A bucket can be configured to save HTTP log information to a sibling bucket; this can be used in [data mining](./Data_mining) operations.[[14]](./Amazon_S3#cite_note-14)

 

Various [User Mode File System (FUSE)](./Filesystem_in_Userspace)–based file systems for [Linux](./Linux) or other Unix-like operating systems can be used to mount an S3 bucket as a file system. The semantics of the Amazon S3 file system are not that of a [POSIX](./POSIX) file system, so the file system may not behave entirely as expected.[[15]](./Amazon_S3#cite_note-15) Implementations include [Rclone](./Rclone) and AWS's own Mountpoint for S3.[[16]](./Amazon_S3#cite_note-16)[[17]](./Amazon_S3#cite_note-17)

 

### Amazon S3 storage classes

 

Amazon S3 offers nine different storage classes with different levels of durability, availability, and performance requirements.[[18]](./Amazon_S3#cite_note-18)

 
- Amazon S3 Standard is the default. It is general purpose storage for frequently accessed data.
- Amazon S3 Express One Zone is a single-digit millisecond latency storage for frequently accessed data and latency-sensitive applications. It stores data only in one availability zone.[[19]](./Amazon_S3#cite_note-19)

 

The Amazon S3 Glacier storage classes above are distinct from [Amazon Glacier](./Amazon_Glacier), which is a separate product with its own APIs.

 

### File size limits

 

An object in S3 can be between 0 bytes and 5 TB. If an object is larger than 5 TB, it must be divided into chunks prior to uploading. When uploading, Amazon S3 allows a maximum of 5 GB in a single upload operation; hence, objects larger than 5 GB must be uploaded via the S3 multipart upload API.[[20]](./Amazon_S3#cite_note-20)

 

### Scale

 

As of 2025, S3 stores 500 trillion objects, 100s of [exabytes](./Exabyte) of data, serves 200 million requests per second,[[21]](./Amazon_S3#cite_note-21) and peaks at about 1 petabyte per second in bandwidth.[[22]](./Amazon_S3#cite_note-22)

 

## Uses

 

### Notable users

 
- Photo hosting service [SmugMug](./SmugMug) has used Amazon S3 since April 2006. They experienced a number of initial outages and slowdowns, but after one year they described it as being "considerably more reliable than our own internal storage" and claimed to have saved almost $1 million in storage costs.[[23]](./Amazon_S3#cite_note-smugmug-smtm-23)
- [Netflix](./Netflix) uses Amazon S3 as their [system of record](./System_of_record). Netflix implemented a tool, S3mper,[[24]](./Amazon_S3#cite_note-S3mper-24) to address the Amazon S3 limitations of [eventual consistency](./Eventual_consistency).[[25]](./Amazon_S3#cite_note-25) S3mper stores the filesystem metadata: filenames, directory structure, and permissions in [Amazon DynamoDB](./Amazon_DynamoDB).[[26]](./Amazon_S3#cite_note-:0-26)
- [Reddit](./Reddit) is hosted on Amazon S3.[[27]](./Amazon_S3#cite_note-reddit_case_study-27)
- [Bitcasa](./Bitcasa),[[28]](./Amazon_S3#cite_note-Bitcasa_Legal-28) and [Tahoe-LAFS](./Tahoe-LAFS)-on-S3,[[29]](./Amazon_S3#cite_note-Tahoe-LAFS-on-S3-29) among others, use Amazon S3 for online backup and synchronization services. In 2016, Dropbox stopped using Amazon S3 services and developed its own cloud server.[[30]](./Amazon_S3#cite_note-30)[[31]](./Amazon_S3#cite_note-31)
- [Swiftype](./Swiftype)'s CEO has mentioned that the company uses Amazon S3.[[32]](./Amazon_S3#cite_note-32)

 

## S3 API and competing services

 

The broad adoption of Amazon S3 and related tooling has given rise to competing services based on the S3 [API.](./Application_programming_interface) These services use the standard programming interface but are differentiated by their underlying technologies and business models.[[33]](./Amazon_S3#cite_note-33) A standard interface enables better competition from rival providers and allows [economies of scale](./Economies_of_scale) in implementation, among other benefits.[[34]](./Amazon_S3#cite_note-34) Users are not required to go directly to Amazon as several storage providers such as [Cloudian](./Cloudian), [Backblaze B2](./Backblaze), [Wasabi](./Wasabi_Technologies) offer S3-compatible storage with options of on-premises and private cloud deployments.[[35]](./Amazon_S3#cite_note-35) Several open-source implementations of S3-compatible object store servers can be self-hosted, such as Garage.[[36]](./Amazon_S3#cite_note-36)[[37]](./Amazon_S3#cite_note-37) [IBM Cloud Object Storage](./IBM_Cloud_Object_Storage) also offers a cloud-based S3-compatible option of Object Storage.[[38]](./Amazon_S3#cite_note-38)

 

## History

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f1/AmazonS3TwoTrillionObjects.JPG/250px-AmazonS3TwoTrillionObjects.JPG)](./File:AmazonS3TwoTrillionObjects.JPG)At AWS Summit 2013 NYC, CTO [Werner Vogels](./Werner_Vogels) announces 2 trillion objects stored in S3. 

Amazon Web Services introduced Amazon S3 in 2006.[[39]](./Amazon_S3#cite_note-39)[[40]](./Amazon_S3#cite_note-40)

 
| Date | Number of Items Stored |
| --- | --- |
| October 2007 | 10 billion[41] |
| January 2008 | 14 billion[41] |
| October 2008 | 29 billion[42] |
| March 2009 | 52 billion[43] |
| August 2009 | 64 billion[44] |
| March 2010 | 102 billion[45] |
| April 2013 | 2 trillion[46] |
| March 2021 | 100 trillion[47] |
| March 2023 | 280 trillion[48] |
| November 2024 | 400 trillion[49] |

 

In November 2017, AWS added default encryption capabilities at bucket level.[[50]](./Amazon_S3#cite_note-50)

 

## See also

 
- [Amazon Elastic Block Store](./Amazon_Elastic_Block_Store) (EBS)
- [Timeline of Amazon Web Services](./Timeline_of_Amazon_Web_Services)

 

## References

 

### Citations

  
1. [1](./Amazon_S3#cite_ref-s3_usa_1-0) [2](./Amazon_S3#cite_ref-s3_usa_1-1) ["Amazon Web Services Launches "Amazon S3""](https://press.aboutamazon.com/news-releases/news-release-details/amazon-web-services-launches-amazon-s3-simple-storage-service) (Press release). 2006-03-14. [Archived](https://web.archive.org/web/20181115112821/https://press.aboutamazon.com/news-releases/news-release-details/amazon-web-services-launches-amazon-s3-simple-storage-service) from the original on 2018-11-15. Retrieved 2018-11-14.
2. [↑](./Amazon_S3#cite_ref-2) Huang, Dijiang; Wu, Huijun (2017-09-08). [*Mobile Cloud Computing: Foundations and Service Models*](https://books.google.com/books?id=dupGDgAAQBAJ). Morgan Kaufmann. p. 67. [ISBN](./ISBN_(identifier)) [9780128096444](./Special:BookSources/9780128096444). [Archived](https://web.archive.org/web/20181115112855/https://books.google.ca/books?id=dupGDgAAQBAJ&source=gbs_navlinks_s) from the original on 2018-11-15. Retrieved 2018-11-15.
3. [1](./Amazon_S3#cite_ref-:1_3-0) [2](./Amazon_S3#cite_ref-:1_3-1) ["Cloud Object Storage - Store & Retrieve Data Anywhere - Amazon Simple Storage Service"](https://aws.amazon.com/s3/). *Amazon Web Services, Inc*. [Archived](https://web.archive.org/web/20180517083922/https://aws.amazon.com/s3/) from the original on 2018-05-17. Retrieved 2018-05-17.
4. [↑](./Amazon_S3#cite_ref-4) ["5 Key Events in the history of Cloud Computing - DZone Cloud"](https://dzone.com/articles/5-key-events-history-cloud). *dzone.com*. [Archived](https://web.archive.org/web/20180929000541/https://dzone.com/articles/5-key-events-history-cloud) from the original on 2018-09-29. Retrieved 2018-09-28.
5. [↑](./Amazon_S3#cite_ref-s3-europe_5-0) ["Amazon Web Services Offers European Storage for Amazon S3"](https://press.aboutamazon.com/news-releases/news-release-details/amazon-web-services-offers-european-storage-amazon-s3) (Press release). 2007-11-06. [Archived](https://web.archive.org/web/20181115112804/https://press.aboutamazon.com/news-releases/news-release-details/amazon-web-services-offers-european-storage-amazon-s3) from the original on 2018-11-15. Retrieved 2018-11-14.
6. [↑](./Amazon_S3#cite_ref-6) ["What is Cloud Object Storage? – AWS"](https://aws.amazon.com/what-is-cloud-object-storage/). *Amazon Web Services, Inc*. 2019-10-16. [Archived](https://web.archive.org/web/20180920181620/https://aws.amazon.com/what-is-cloud-object-storage/) from the original on 2018-09-20. Retrieved 2018-07-09.
7. [↑](./Amazon_S3#cite_ref-7) ["Tech Blog » Starting Websphere in Cloud and saving the data in S3"](https://web.archive.org/web/20100312080332/http://techblog.aasisvinayak.com/starting-websphere-in-cloud-and-saving-the-data-in-s3). *techblog.aasisvinayak.com*. Archived from [the original](http://techblog.aasisvinayak.com/starting-websphere-in-cloud-and-saving-the-data-in-s3/) on 2010-03-12.
8. [↑](./Amazon_S3#cite_ref-8) ["open-guides/og-aws"](https://github.com/open-guides/og-aws/blob/master/README.md#s3). *GitHub*. [Archived](https://web.archive.org/web/20180103123141/https://github.com/open-guides/og-aws/blob/master/README.md#s3) from the original on 2018-01-03. Retrieved 2018-05-17.
9. [↑](./Amazon_S3#cite_ref-9) ["Error Responses - Amazon Simple Storage Service"](https://docs.aws.amazon.com/AmazonS3/latest/API/ErrorResponses.html). *docs.aws.amazon.com*. [Archived](https://web.archive.org/web/20171224010324/http://docs.aws.amazon.com/AmazonS3/latest/API/ErrorResponses.html) from the original on 2017-12-24. Retrieved 2018-05-21.
10. [↑](./Amazon_S3#cite_ref-10) ["Using versioning in S3 buckets - Amazon Simple Storage Service"](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html). [Archived](https://web.archive.org/web/20220222091551/https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html) from the original on 2022-02-22. Retrieved 2022-02-22.
11. [↑](./Amazon_S3#cite_ref-11) ["Introduction to Amazon S3 - Amazon Simple Storage Service"](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html). *docs.aws.amazon.com*. [Archived](https://web.archive.org/web/20180512235723/https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html) from the original on 2018-05-12. Retrieved 2018-05-17.
12. [↑](./Amazon_S3#cite_ref-S3_Web_Hosting_12-0) ["How to use Amazon S3 for Web Hosting"](https://web.archive.org/web/20080408024708/http://www.bucketexplorer.com/documentation/amazon-s3--how-to-use-Amazon-s3-for-web-hosting.html). *bucketexplorer.com*. Archived from [the original](http://www.bucketexplorer.com/documentation/amazon-s3--how-to-use-Amazon-s3-for-web-hosting.html) on 2008-04-08. Retrieved 2008-05-06.
13. [↑](./Amazon_S3#cite_ref-13) [Amazon Simple Storage Service](http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?WebsiteHosting.html) [Archived](https://web.archive.org/web/20110220042555/http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?WebsiteHosting.html) 2011-02-20 at the [Wayback Machine](./Wayback_Machine) Docs.amazonwebservices.com. Retrieved on 2013-08-09.
14. [↑](./Amazon_S3#cite_ref-14) [http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) [Archived](https://web.archive.org/web/20141223092055/http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) 2014-12-23 at the [Wayback Machine](./Wayback_Machine) Server Access Logging
15. [↑](./Amazon_S3#cite_ref-15) ["Comparison of S3QL and other S3 file systems"](https://code.google.com/p/s3ql/wiki/other_s3_filesystems). [Archived](https://web.archive.org/web/20120805030057/http://code.google.com/p/s3ql/wiki/other_s3_filesystems) from the original on 2012-08-05. Retrieved 2012-06-29.
16. [↑](./Amazon_S3#cite_ref-16) Craig-Wood, Nick. ["rclone mount"](https://rclone.org/commands/rclone_mount/). *Rclone*. Retrieved 2025-11-16.
17. [↑](./Amazon_S3#cite_ref-17) [*awslabs/mountpoint-s3*](https://github.com/awslabs/mountpoint-s3), Amazon Web Services - Labs, 2025-11-15, retrieved 2025-11-16
18. [↑](./Amazon_S3#cite_ref-18) ["Cloud Storage Classes – Amazon Simple Storage Service (S3) – AWS"](https://aws.amazon.com/s3/storage-classes/). *Amazon Web Services, Inc*. [Archived](https://web.archive.org/web/20180613200647/https://aws.amazon.com/s3/storage-classes/) from the original on 2018-06-13. Retrieved 2018-05-17.
19. [↑](./Amazon_S3#cite_ref-19) ["Announcing the new Amazon S3 Express One Zone high performance storage class | AWS News Blog"](https://aws.amazon.com/blogs/aws/new-amazon-s3-express-one-zone-high-performance-storage-class/). *aws.amazon.com*. 2023-11-28. Retrieved 2023-12-01.
20. [↑](./Amazon_S3#cite_ref-20) ["How to Upload Large Files to S3"](https://web.archive.org/web/20221001213248/https://riyanchristy.goseeq.net/how-to-upload-large-files-to-s3-efficiently/). June 21, 2022. Archived from [the original](https://riyanchristy.goseeq.net/how-to-upload-large-files-to-s3-efficiently/) on October 1, 2022. Retrieved June 22, 2022.
21. [↑](./Amazon_S3#cite_ref-21) Garman, Matt. [*AWS re:Invent 2025 - Keynote with CEO Matt Garman*](https://www.youtube.com/watch?v=q3Sb9PemsSo&t=234). [Las Vegas](./Las_Vegas): Amazon.
22. [↑](./Amazon_S3#cite_ref-22) [*AWS re:Invent 2024 - Dive deep on Amazon S3 (STG302)*](https://www.youtube.com/watch?v=NXehLy7IiPM). *youtube.com*. 5 Dec 2024.  Event occurs at 2m.
23. [↑](./Amazon_S3#cite_ref-smugmug-smtm_23-0) ["Amazon S3: Show Me the Money"](https://donmacaskill.wordpress.com/2006/11/10/amazon-s3-show-me-the-money/). *SmugMug Blog*. SmugMug. November 10, 2006. [Archived](https://web.archive.org/web/20170303130206/https://donmacaskill.wordpress.com/2006/11/10/amazon-s3-show-me-the-money/) from the original on 2017-03-03. Retrieved 2017-03-03.
24. [↑](./Amazon_S3#cite_ref-S3mper_24-0) ["S3mper: Consistency in the Cloud"](http://techblog.netflix.com/2014/01/s3mper-consistency-in-cloud.html). [Archived](https://web.archive.org/web/20160424205437/http://techblog.netflix.com/2014/01/s3mper-consistency-in-cloud.html) from the original on 2016-04-24. Retrieved 2016-05-01.
25. [↑](./Amazon_S3#cite_ref-25) ["Introduction to Amazon S3"](http://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html). *Amazon*. [Archived](https://web.archive.org/web/20171225230323/http://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html) from the original on 2017-12-25. Retrieved 28 December 2017.
26. [↑](./Amazon_S3#cite_ref-:0_26-0) Hern, Alex (2017-02-02). ["Amazon Web Services: the secret to the online retailer's future success"](https://www.theguardian.com/technology/2017/feb/02/amazon-web-services-the-secret-to-the-online-retailers-future-success). *the Guardian*. [Archived](https://web.archive.org/web/20180502223750/https://www.theguardian.com/technology/2017/feb/02/amazon-web-services-the-secret-to-the-online-retailers-future-success) from the original on 2018-05-02. Retrieved 2018-04-23.
27. [↑](./Amazon_S3#cite_ref-reddit_case_study_27-0) ["AWS Case Study: reddit"](http://aws.amazon.com/solutions/case-studies/reddit/). *aws.amazon.com*. 2015. [Archived](https://web.archive.org/web/20150317005440/http://aws.amazon.com/solutions/case-studies/reddit/) from the original on 2015-03-17. Retrieved March 18, 2015.
28. [↑](./Amazon_S3#cite_ref-Bitcasa_Legal_28-0) ["Bitcasa Legal"](https://www.bitcasa.com/legal). May 16, 2013. Retrieved 2013-05-16.`{{cite web}}`:  CS1 maint: deprecated archival service ([link](./Category:CS1_maint:_deprecated_archival_service))
29. [↑](./Amazon_S3#cite_ref-Tahoe-LAFS-on-S3_29-0) ["What is Tahoe-LAFS-on-S3?"](https://leastauthority.com/products). August 21, 2012. [Archived](https://web.archive.org/web/20130506021742/https://leastauthority.com/products) from the original on 2013-05-06. Retrieved 2012-08-21.
30. [↑](./Amazon_S3#cite_ref-30) ["The Epic Story of Dropbox's Exodus From the Amazon Cloud Empire"](https://www.wired.com/2016/03/epic-story-dropboxs-exodus-amazon-cloud-empire/). *WIRED*. [Archived](https://web.archive.org/web/20180125195150/https://www.wired.com/2016/03/epic-story-dropboxs-exodus-amazon-cloud-empire/) from the original on 2018-01-25. Retrieved 2018-04-23.
31. [↑](./Amazon_S3#cite_ref-31) ["Dropbox saved almost $75 million over two years by building its own tech infrastructure"](https://www.geekwire.com/2018/dropbox-saved-almost-75-million-two-years-building-tech-infrastructure/). *GeekWire*. 2018-02-23. [Archived](https://web.archive.org/web/20180423170423/https://www.geekwire.com/2018/dropbox-saved-almost-75-million-two-years-building-tech-infrastructure/) from the original on 2018-04-23. Retrieved 2018-04-23.
32. [↑](./Amazon_S3#cite_ref-32) ["Swiftype Explains Their Cloud Stack"](http://stackshare.io/posts/swiftype-explains-their-cloud-stack). July 1, 2013. [Archived](https://web.archive.org/web/20141208083021/http://stackshare.io/posts/swiftype-explains-their-cloud-stack) from the original on 2014-12-08. Retrieved 2014-12-08.
33. [↑](./Amazon_S3#cite_ref-33) Watters, Audrey (12 July 2010). ["Cloud Community Debates, Is Amazon S3's API the Standard? (And Should It Be?)"](https://web.archive.org/web/20130217035941/http://readwrite.com/2010/07/12/cloud-community-debates-is-ama). SAY Media, Inc. Archived from the original on 2013-02-17. Retrieved 19 December 2012.
34. [↑](./Amazon_S3#cite_ref-34) [*Crossroads of Information Technology Standards*](http://www.nap.edu/openbook.php?record_id=10440&page=36). Committee on Standards Workshop Planning, Board on Telecommunications and Computer Applications, Commission on Engineering and Technical Systems, National Research Council. Washington, DC: The National Academies Press, 1990. 1990. pp. 36–37. [doi](./Doi_(identifier)):[10.17226/10440](https://doi.org/10.17226%2F10440). [ISBN](./ISBN_(identifier)) [978-0-309-58171-4](./Special:BookSources/978-0-309-58171-4). [Archived](https://web.archive.org/web/20140325160847/http://www.nap.edu/openbook.php?record_id=10440&page=36) from the original on 2014-03-25. Retrieved 2014-03-25.`{{cite book}}`:  CS1 maint: others ([link](./Category:CS1_maint:_others))
35. [↑](./Amazon_S3#cite_ref-35) ["How to use S3-compatible storage | TechTarget"](https://www.techtarget.com/searchstorage/tip/How-to-use-S3-compatible-storage). *Search Storage*. Retrieved 2025-08-09.
36. [↑](./Amazon_S3#cite_ref-36) Yegulalp, Serdar (2017-01-31). ["Google Go-powered object storage server offers open source AWS alternative"](https://www.infoworld.com/article/2252410/google-go-powered-object-storage-server-offers-open-source-aws-alternative.html). *InfoWorld*. Retrieved 2025-11-16.
37. [↑](./Amazon_S3#cite_ref-37) Bhutani, Dhruv (2025-10-27). ["Stop using MinIO, and use this free, user-friendly tool instead"](https://www.xda-developers.com/stop-using-minio-and-use-this-free-user-friendly-tool-instead/). *XDA*. Retrieved 2025-11-16. 
38. [↑](./Amazon_S3#cite_ref-38) ["IBM Cloud Object Storage S3 API | Introduction on IBM Cloud API Docs"](https://cloud.ibm.com/apidocs/cos/cos-compatibility).
39. [↑](./Amazon_S3#cite_ref-39) Overview of Amazon Web Services, 2018, [https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html) [Archived](https://web.archive.org/web/20171118025949/https://d1.awsstatic.com/whitepapers/aws-overview.pdf) 2017-11-18 at the [Wayback Machine](./Wayback_Machine)
40. [↑](./Amazon_S3#cite_ref-40) Garfinkel, Simson L. 2007. An Evaluation of Amazon's Grid Computing Services: EC2, S3, and SQS. Harvard Computer Science Group Technical Report TR-08-07. [https://dash.harvard.edu/bitstream/handle/1/24829568/tr-08-07.pdf?sequence=1](https://dash.harvard.edu/bitstream/handle/1/24829568/tr-08-07.pdf?sequence=1) [Archived](https://web.archive.org/web/20180729230848/https://dash.harvard.edu/bitstream/handle/1/24829568/tr-08-07.pdf?sequence=1) 2018-07-29 at the [Wayback Machine](./Wayback_Machine)
41. [1](./Amazon_S3#cite_ref-amzn-cto-blog_41-0) [2](./Amazon_S3#cite_ref-amzn-cto-blog_41-1) Vogels, Werner (2008-03-19). ["Happy Birthday, Amazon S3!"](http://www.allthingsdistributed.com/2008/03/happy_birthday_amazon_s3.html). *All Things Distributed*. [Archived](https://web.archive.org/web/20080509070955/http://www.allthingsdistributed.com/2008/03/happy_birthday_amazon_s3.html) from the original on 2008-05-09. Retrieved 2008-05-23.
42. [↑](./Amazon_S3#cite_ref-busier_42-0) ["Amazon S3 - Busier Than Ever"](https://web.archive.org/web/20081011012039/http://aws.typepad.com/aws/2008/10/amazon-s3---now.html). 2008-10-08. Archived from [the original](http://aws.typepad.com/aws/2008/10/amazon-s3---now.html) on 2008-10-11. Retrieved 2008-10-09.
43. [↑](./Amazon_S3#cite_ref-43) ["Celebrating S3's Third Birthday With Special Anniversary Pricing - Amazon Web Services"](http://aws.typepad.com/aws/2009/03/celebrating-s3s-third-birthday-with-an-upload-promotion.html). *typepad.com*. 31 March 2009. [Archived](https://web.archive.org/web/20110707102355/http://aws.typepad.com/aws/2009/03/celebrating-s3s-third-birthday-with-an-upload-promotion.html) from the original on 2011-07-07. Retrieved 2009-04-01.
44. [↑](./Amazon_S3#cite_ref-44) ["Amazon's Head Start in the Cloud Pays Off"](http://www.eweek.com/c/a/Cloud-Computing/Amazons-Head-Start-in-the-Cloud-Pays-Off-584083/). *eweek.com*.`{{cite web}}`:  CS1 maint: deprecated archival service ([link](./Category:CS1_maint:_deprecated_archival_service))
45. [↑](./Amazon_S3#cite_ref-45) ["Amazon S3 Now Hosts 100 Billion Objects"](http://www.datacenterknowledge.com/archives/2010/03/09/amazon-s3-now-hosts-100-billion-objects/). *datacenterknowledge.com*. 9 March 2010. [Archived](https://web.archive.org/web/20100312102850/http://www.datacenterknowledge.com/archives/2010/03/09/amazon-s3-now-hosts-100-billion-objects/) from the original on 2010-03-12. Retrieved 2010-03-09.
46. [↑](./Amazon_S3#cite_ref-aws.typepad.com_46-0) ["Amazon S3 – Two Trillion Objects, 1.1 Million Requests / Second - Amazon Web Services"](http://aws.typepad.com/aws/2013/04/amazon-s3-two-trillion-objects-11-million-requests-second.html). *typepad.com*. 18 April 2013. [Archived](https://web.archive.org/web/20130930043059/http://aws.typepad.com/aws/2013/04/amazon-s3-two-trillion-objects-11-million-requests-second.html) from the original on 30 September 2013. Retrieved 4 October 2013.
47. [↑](./Amazon_S3#cite_ref-aws.amazon.com_2021_47-0) ["Celebrate 15 Years of Amazon S3 with 'Pi Week' Livestream Events"](https://aws.amazon.com/blogs/aws/amazon-s3s-15th-birthday-it-is-still-day-1-after-5475-days-100-trillion-objects/). *amazon.com*. 14 March 2021.
48. [↑](./Amazon_S3#cite_ref-aws.amazon.com_2023_48-0) ["Celebrate Amazon S3's 17th birthday at AWS Pi Day 2023"](https://aws.amazon.com/blogs/aws/celebrate-amazon-s3s-17th-birthday-at-aws-pi-day-2023/). *amazon.com*. 14 March 2023.
49. [↑](./Amazon_S3#cite_ref-49) ["Adapting to change with data patterns on AWS: The "aggregate" cloud data pattern | AWS Storage Blog"](https://aws.amazon.com/blogs/storage/adapting-to-change-with-data-patterns-on-aws-the-aggregate-cloud-data-pattern/). 20 December 2024.
50. [↑](./Amazon_S3#cite_ref-50) ["AWS re:Invent 2024 - Dive deep on Amazon S3 (STG302)"](https://www.youtube.com/watch?v=NXehLy7IiPM&list=PL2yQDdvlhXf_ZsP25dGLTNbrVSphM2JDl&index=666). *[YouTube](./YouTube)*. 9 December 2024.

 

### Sources

  
- ["Server Access Logging"](http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html). [Archived](https://web.archive.org/web/20141223092055/http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) from the original on 2014-12-23. Retrieved 2014-12-23.
- ["Amazon S3 Developer Guide"](http://docs.amazonwebservices.com/AmazonS3/latest/dev/). 2006-03-01.
- ["Amazon S3 Introduces Storage Pricing Tiers"](http://developer.amazonwebservices.com/connect/ann.jspa?annID=351). 2008-10-08.
- ["RightScale Ruby library to access Amazon CloudFront, EC2, S3, SQS, and SDB"](https://web.archive.org/web/20081103070950/http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1014). 2007-10-27. Archived from [the original](http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1014) on 2008-11-03. Retrieved 2009-01-07.

  

## External links

 
- [Open Source Alternatives To Amazon S3](https://opensourcealternative.to/alternativesto/amazon-s3)
- [European alternatives to Amazon S3](https://european-alternatives.eu/alternative-to/amazon-s3)
- [Amazon S3 Alternatives for Modern Cloud Storage](https://www.digitalocean.com/resources/articles/amazon-s3-alternatives)

 

 

  
| vteAmazon |
| --- |
| People | CurrentJeff Bezos(Founder and Executive Chairman)Andy Jassy(President and CEO)Werner Vogels(CTO)FormerRick DalzellPaul DavisTony HsiehChristopher NorthRam ShriramTom SzkutakBrian Valentine | Current | Jeff Bezos(Founder and Executive Chairman)Andy Jassy(President and CEO)Werner Vogels(CTO) | Former | Rick DalzellPaul DavisTony HsiehChristopher NorthRam ShriramTom SzkutakBrian Valentine |
| Current | Jeff Bezos(Founder and Executive Chairman)Andy Jassy(President and CEO)Werner Vogels(CTO) |
| Former | Rick DalzellPaul DavisTony HsiehChristopher NorthRam ShriramTom SzkutakBrian Valentine |
| Facilities | DopplerDay 1HQ2Principal PlaceSpheresBellevue 600 |
| Products andservices | SubsidiariesAbeBooksAmazon Game StudiosAmazon Lab126Amazon LeoAmazon PharmacyPillPackAmazon RoboticsAmazon University EsportsAnnapurna LabsAudibleBlink HomeBody LabsBookFinderFreshGoodreadsGoodreads Choice AwardsGraphiqIMDbBox Office MojoIMDbProOne MedicalRingNeighborsShopbopTwitchIGDBWoot.comZapposZooxCloudcomputingWeb ServicesAMIAmazon AuroraBeanstalkCloudFrontDynamoDBEBSEC2EFSElastiCacheEMRGlacierGlueLambdaLightsailMTurkNeptuneProduct Advertising APIRDSRedshiftRekognitionRoute 53S3SageMakerSESSNSSimpleDBSQSVPCServicesAmazon.comChinaAlexaAppstoreDigital Game StoreFire OSKindle StoreLunaPaymentsPrimeAmazon miniTVMX PlayerKeyPrime MusicPrime NowPrime PantryPrime VideoSportsMarketplaceMusic(Wondery)SilkWirelessDevicesAstroEchoShowEcho BudsFireFire HDFire HDXFire TVStickKindleTechnology1-ClickAmazon OneDynamoObidosLumberyardMediaAmazon GamesAmazon PublishingBreakthrough Novel AwardBest Books of the YearAmazon MGM StudiosMetro-Goldwyn-MayerUnited ArtistsOrion PicturesAmerican International PicturesMGM+Kindle Direct PublishingYES Network(15%)RetailWhole Foods MarketLogisticsAmazon FreightAmazon AirAmazon Prime AirFormer43 ThingsA9.comAskvilleAlexa InternetAmapediaAmazon BooksAmazon ClinicAmazon FreshAmazon GoAmie Street(Songza)Book DepositoryCDNowComiXologyDash buttonsDash wandDiapers.comDigital Photography ReviewDouble Helix GamesDriveEndless.comFire PhoneFreeveeLexcycleLiquavistaLivingSocialLoveFilmMGM HoldingsMobipocketPlanetAllReflexive EntertainmentSellabandShelfariSouq.comTenMarksTreasure TruckWithoutabox | Subsidiaries | AbeBooksAmazon Game StudiosAmazon Lab126Amazon LeoAmazon PharmacyPillPackAmazon RoboticsAmazon University EsportsAnnapurna LabsAudibleBlink HomeBody LabsBookFinderFreshGoodreadsGoodreads Choice AwardsGraphiqIMDbBox Office MojoIMDbProOne MedicalRingNeighborsShopbopTwitchIGDBWoot.comZapposZoox | Cloudcomputing | Web ServicesAMIAmazon AuroraBeanstalkCloudFrontDynamoDBEBSEC2EFSElastiCacheEMRGlacierGlueLambdaLightsailMTurkNeptuneProduct Advertising APIRDSRedshiftRekognitionRoute 53S3SageMakerSESSNSSimpleDBSQSVPC | Services | Amazon.comChinaAlexaAppstoreDigital Game StoreFire OSKindle StoreLunaPaymentsPrimeAmazon miniTVMX PlayerKeyPrime MusicPrime NowPrime PantryPrime VideoSportsMarketplaceMusic(Wondery)SilkWireless | Devices | AstroEchoShowEcho BudsFireFire HDFire HDXFire TVStickKindle | Technology | 1-ClickAmazon OneDynamoObidosLumberyard | Media | Amazon GamesAmazon PublishingBreakthrough Novel AwardBest Books of the YearAmazon MGM StudiosMetro-Goldwyn-MayerUnited ArtistsOrion PicturesAmerican International PicturesMGM+Kindle Direct PublishingYES Network(15%) | Retail | Whole Foods Market | Logistics | Amazon FreightAmazon AirAmazon Prime Air | Former | 43 ThingsA9.comAskvilleAlexa InternetAmapediaAmazon BooksAmazon ClinicAmazon FreshAmazon GoAmie Street(Songza)Book DepositoryCDNowComiXologyDash buttonsDash wandDiapers.comDigital Photography ReviewDouble Helix GamesDriveEndless.comFire PhoneFreeveeLexcycleLiquavistaLivingSocialLoveFilmMGM HoldingsMobipocketPlanetAllReflexive EntertainmentSellabandShelfariSouq.comTenMarksTreasure TruckWithoutabox |
| Subsidiaries | AbeBooksAmazon Game StudiosAmazon Lab126Amazon LeoAmazon PharmacyPillPackAmazon RoboticsAmazon University EsportsAnnapurna LabsAudibleBlink HomeBody LabsBookFinderFreshGoodreadsGoodreads Choice AwardsGraphiqIMDbBox Office MojoIMDbProOne MedicalRingNeighborsShopbopTwitchIGDBWoot.comZapposZoox |
| Cloudcomputing | Web ServicesAMIAmazon AuroraBeanstalkCloudFrontDynamoDBEBSEC2EFSElastiCacheEMRGlacierGlueLambdaLightsailMTurkNeptuneProduct Advertising APIRDSRedshiftRekognitionRoute 53S3SageMakerSESSNSSimpleDBSQSVPC |
| Services | Amazon.comChinaAlexaAppstoreDigital Game StoreFire OSKindle StoreLunaPaymentsPrimeAmazon miniTVMX PlayerKeyPrime MusicPrime NowPrime PantryPrime VideoSportsMarketplaceMusic(Wondery)SilkWireless |
| Devices | AstroEchoShowEcho BudsFireFire HDFire HDXFire TVStickKindle |
| Technology | 1-ClickAmazon OneDynamoObidosLumberyard |
| Media | Amazon GamesAmazon PublishingBreakthrough Novel AwardBest Books of the YearAmazon MGM StudiosMetro-Goldwyn-MayerUnited ArtistsOrion PicturesAmerican International PicturesMGM+Kindle Direct PublishingYES Network(15%) |
| Retail | Whole Foods Market |
| Logistics | Amazon FreightAmazon AirAmazon Prime Air |
| Former | 43 ThingsA9.comAskvilleAlexa InternetAmapediaAmazon BooksAmazon ClinicAmazon FreshAmazon GoAmie Street(Songza)Book DepositoryCDNowComiXologyDash buttonsDash wandDiapers.comDigital Photography ReviewDouble Helix GamesDriveEndless.comFire PhoneFreeveeLexcycleLiquavistaLivingSocialLoveFilmMGM HoldingsMobipocketPlanetAllReflexive EntertainmentSellabandShelfariSouq.comTenMarksTreasure TruckWithoutabox |
| Litigation | Perfect 10, Inc. v. Amazon.com, Inc.Amazon.com, Inc. v. Barnesandnoble.com, Inc.Amazon.com Inc v Canada (Commissioner of Patents)FTC v. Amazon |
| Other | Amazon LightASINCommunity Banana StandCriticism(tax)FishbowlHistory of AmazonLibraryThingList of Amazon brandsList of Amazon products and servicesList of mergers and acquisitions by AmazonLockerMacKenzie ScottStatistically improbable phraseVineWorker organizationList of fatalitiesEdwardsville Amazon warehouse collapse |
| Unions | Congress of Essential WorkersAmazon Labor UnionAmazon worker organization2024 strike |
| Category |

 
| vteCloud computing |
| --- |
| Business models | Content as a serviceData as a serviceDesktop as a serviceFunction as a serviceInfrastructure as a serviceIntegration platform as a serviceBackend as a serviceNetwork as a servicePlatform as a serviceSecurity as a serviceSoftware as a service |
| Technologies | Cloud databaseCloud-native computingCloud storageCloud storage gatewaysData centersDew computingDistributed file system for cloudHardware virtualizationInternetMobile cloud computingNative cloud applicationNetworkingPersonal cloudSecurityServerless computingStructured storageVirtual applianceWeb APIsVirtual private cloud |
| Applications | BoxDropboxGoogleWorkspaceDriveHP Cloud(closed)IBM CloudLarkMicrosoftOffice 365OneDriveNextcloudOpenDeskOracle CloudOwncloudProton DriveRackspaceSalesforceSeafilePlateSpinWorkdayZoho |
| Platforms | Alibaba CloudAmazon Web ServicesAppScaleBoxCloudBoltCloud FoundryCocaine (PaaS)Engine YardHelionGE PredixGoogle App EngineGreenQloudHerokuIBM CloudInktankJelasticMicrosoft AzureMindSphereNetlifyOracle CloudOutSystemsopenQRMOpenShiftPythonAnywhereRightScaleScalrForce.comSAP Business Technology PlatformSplunkVercelvCloud AirWaveMaker |
| Infrastructure | Alibaba CloudAmazon Web ServicesAbiquo Enterprise EditionCloudStackCitrix CloudDeftDigitalOceanEMC AtmosEucalyptusFujitsuGoogle CloudGreenButtonGreenQloudIBM CloudilandJoyentLinodeLunacloudMicrosoft AzureMirantisNetlifyNimbulaNimbusOpenIOOpenNebulaOpenStackOracle CloudOrionVMRackspace CloudSafe Swiss CloudZadaralibvirtlibguestfsOVirtVirtual Machine ManagerWakame-vdcVercelVirtual Private Cloud OnDemand |
| CategoryCommons |