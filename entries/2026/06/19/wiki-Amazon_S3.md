---
source: sources/wiki-Amazon_S3.md
source_url: https://en.wikipedia.org/wiki/Amazon_S3
---

## Amazon S3 (Simple Storage Service) — Object Storage Fundamentals

Amazon S3 is AWS's core object storage service, launched March 14, 2006. It provides highly scalable, durable, low-latency storage through a web service interface. S3 uses the same infrastructure as Amazon.com's e-commerce platform and supports use cases including internet application storage, backups, disaster recovery, data archives, data lakes for analytics, and hybrid cloud storage. As of 2025, S3 stores 500 trillion objects across hundreds of exabytes, serving 200 million requests per second with peak bandwidth of ~1 PB/s.

## Key Concepts

- **Object storage architecture**: Data is stored as objects (not blocks or files), organized into buckets. Each object is identified by a unique user-assigned key.
- **Objects**: Can range from 0 bytes to 5 TB in size. Single upload operations are limited to 5 GB — objects larger than 5 GB require the multipart upload API.
- **Buckets**: The top-level container for objects. Managed via AWS Console, SDK, or REST API.
- **Access control**: Requests authorized via access control lists (ACLs) associated with each bucket.
- **Versioning**: Supported but disabled by default.
- **Default encryption**: Available at bucket level (added November 2017).
- **Durability design goals**: High durability (commonly cited as 99.999999999% / "eleven nines"), high availability, low latency, and scalability.
- **Static web hosting**: S3 can serve HTTP-accessible objects, including index and error document support, replacing traditional static web hosting.
- **Authenticated URLs**: Time-limited signed URLs for secure access to private objects.
- **BitTorrent support**: Any S3 object can be served as a BitTorrent feed, reducing bandwidth costs for popular downloads.
- **Server access logging**: Bucket HTTP logs can be saved to a sibling bucket for data mining.
- **FUSE mounting**: S3 buckets can be mounted as filesystems on Linux/Unix via tools like Rclone or AWS Mountpoint for S3, though semantics are not fully POSIX-compliant.

## Storage Classes

Nine storage classes exist, including:
- **S3 Standard** (default) — general purpose, frequently accessed data
- **S3 Express One Zone** — single-digit millisecond latency, single AZ only, for latency-sensitive applications
- **S3 Glacier classes** — archival tiers (distinct from the legacy Amazon Glacier product with its own APIs)

## Commands and Syntax

- **Multipart upload**: Required for objects > 5 GB; single PUT limited to 5 GB per operation
- **Management interfaces**: AWS Console, AWS SDK (programmatic), REST API
- **Bucket logging**: Configure a bucket to write access logs to a sibling bucket

## Relationships

- **AWS ecosystem**: S3 is foundational to AWS alongside EC2. Integrates with DynamoDB (used by Netflix's S3mper for filesystem metadata), CloudFront (CDN), Lambda, Glacier, and other services.
- **S3 API as de facto standard**: The S3 API has become the standard interface for object storage. Competing/compatible services include Cloudian, Backblaze B2, Wasabi, IBM Cloud Object Storage, MinIO, and the open-source Garage project.
- **Eventual consistency**: S3 historically used eventual consistency (Netflix built S3mper to address this). AWS later introduced strong read-after-write consistency.
- **Data lakes**: S3 is the standard storage layer for AWS analytics and data lake architectures.
- **Amazon EBS**: Block storage complement to S3's object storage within AWS.

## Exam-Relevant Points

- **Maximum object size**: 5 TB. Maximum single upload: 5 GB. Objects > 5 GB require multipart upload.
- **Versioning is off by default** — must be explicitly enabled per bucket.
- **Nine storage classes** with varying durability, availability, and performance characteristics.
- **S3 Express One Zone**: Single AZ only — trades availability/durability for single-digit ms latency.
- **S3 Glacier storage classes are distinct from legacy Amazon Glacier** (separate product, separate APIs).
- **Default encryption at bucket level** available since November 2017.
- **S3 can host static websites** with index and error document support.
- **S3 is not a POSIX filesystem** — FUSE-based mounts will not behave identically to local filesystems.
- **Scale numbers** (2025): 500 trillion objects, hundreds of exabytes, 200M requests/sec, ~1 PB/s peak bandwidth.
- **S3 API compatibility**: Know that third-party and open-source alternatives implement the S3 API — relevant to multi-cloud and vendor lock-in discussions.
- **Access control via ACLs** on buckets (also IAM policies and bucket policies in practice).
- **Launched March 14, 2006** — one of the original AWS services.
