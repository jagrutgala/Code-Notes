# Google Cloud Storage Services

Google Cloud provides multiple services with different capabilities and storage capacity. The main types of storages are: Block Storage, File/Object Storage and Database.

List of Googles Storage Services (covered here):

1. [Persistent Disks](#persistent-disks)
1. [Local SSDs](#local-ssds)
1. [Filestore](#filestore)
1. [Cloud Storage](#cloud-storage)
1. [Cloud SQL](#cloud-sql)
1. [Cloud Spanner](#cloud-spanner)
1. [Cloud FireStore](#cloud-firestore)
1. [Cloud BigTable](#cloud-bigtable)
1. [Cloud MemoryStore](#cloud-memorystore)
1. [Cloud BigQuery](#cloud-bigquery)

In Google Cloud's storage services are mainly categorized into 4 types:

1. Block Storage
1. Network Attached Storage (NAS)
1. Object Storage
1. Database

## Persistent Disks

Persistent Disks (PD) are block storage solutions, they essentially allow you to attach super-fast external HDD/SSD over the network to your compute instance. A persistent disk can connect to at most 1 compute instance, but you can attach multiple persistent disks to a compute instance.

Google Cloud offers Persistent Disks in tiered fashion.

- **Standard**: It is a basic HDD but is cost-effective and fast at sequential IO.
- **SSD**: It is a high spec SSD that is expensive, but with a high performance in sequential and random IO.
- **Balanced**: It is also a SSD but it fits in between the Standard and SSD in terms of cost and its capabilities. It is the most recommended on that satisfies most of the use cases.

For good practice you would want to take regular backups of your Persistent Disks. Google Cloud provides you with 2 ways:

- **Snapshots**: Snapshots take a incremental point in time of the persistent disks. It can be scheduled to be taken automatically. It is very fast to create a snapshot from a persistent disk than to create a persistent disk from a snapshot.
- **Images**: Images copy the entire disk capturing the OS if it is a boot disk and any other softwares installed and data stored on it. Disk Images are immutable. It takes longer to create a image from a disk than to create a disk from a image. It is a tool for more of creating disks than to take backup.

**Snapshots VS Custom Images VS Machine Image**

| Use-Case                 | Snapshots          | Custom Images      | Machine Image      |
|--------------------------|--------------------|--------------------|--------------------|
| single disk backup       | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| multi disk backup        | :x:                | :x:                | :white_check_mark: |
| differential disk backup | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| clone disk               | :x:                | :white_check_mark: | :white_check_mark: |
| VM Machine Configuration | :x:                | :x:                | :white_check_mark: |



## Local SSDs
Local SSDs are block storage solutions, they essentially allow you to physically attach super-fast external SSD to your compute instance. A local SSD can connect to at most 1 compute instance, but you can attach multiple persistent disks to a compute instance.

Local SSDs are ephemeral in nature, that means when the VM is stopped/suspended the data in attached SSD is also lost. It is really recommended for high performance, low latency and non-critical data. For example: cache or scratch files.

Another feature of local SSD is automatic encryption, with the catch being encryption keys will be google managed via Cloud KMS.



## Filestore
<!-- TODO - Filestore + Features -->



## Cloud Storage
<!-- TODO - Cloud Storage + Features -->
<!-- TODO - Object Lifecycle Management -->
<!-- TODO - gsutil CLI -->



## Databases
Databases provide an organized & persistent storage of data. It also provides very efficient ways to fetch/query the necessary data.

<!-- Database Category and Metrics -->
<!-- Database Best Practices -->



## Cloud SQL
Cloud SQL is a OLTP relational DB solution provided by Google Cloud. It has an availability of 99.95% & is recommended for up to a few TBs.

**Cloud SQL Features**:
- Regional/Multi-Zonal database service.
- Supports MySql, PostgresSql, T-Sql.
- Automatic backups and binary logging.
- Failover switch to standby instance.
- Read-replica instance creation.
- Automatic encryption of backup & tables.
- Data migration support using Database Migration Service.
- Ability to import and export data using Google Cloud Console.

You can get a pretty high availability & failover support using the following:
- Enable automatic backups & binary logging.
- Create standby instance with auto failover.

> Important Note
> Event after the primary database instance recovers after the failover happens the connections don't automatically transfer back to primary instance.
> You can connect to only 1 instance at a time, that is primary or standby. When the primary database instance is active the data is synchronously replicated to the standby instance but is not accessible from the outside until the failover.
> If you have a read heavy requirement then creating a read replica is recommended.



## Cloud Spanner
Cloud Spanner is "Fully Managed", highly available globally distributed SQL database. It is recommend for global and very large data in starting in TBs or PBs.

**Cloud Spanner Features**:
- Global/Multi-Regional database service.
- Highly available with availability of 99.999%.
- Automatic sharding.
- Scales horizontally for read as well as writes.
- Expensive compared to Cloud SQL.
- Ability to export data available via Google Cloud Console.



## Cloud FireStore
Cloud FireStore is a highly scalable NoSQL document database. It is recommended for up to a few TBs.

Cloud FireStore is a upgraded version of DataStore. FireStore instance is available in 2 modes: 1. Native mode 2. DataStore mode
Native Mode is recommended for new projects. DataStore Mode is recommended for migrating existing projects.

**Cloud FireStore Features**:
- Highly scalable document database, automatically scales & partitions.
- Hierarchial storage structure.
- Supports Transactions, Indexes, Sql like queries (GQL).
- Does not support Joins & Aggregates.
- Automatic index creation on single fields. Manually create composite indexes with 2 or more fields.
- Ability to export data available via Google Cloud Storage.
- Supports offline mode with data sync across multiple devices.
- Client side libraries available for Web, Android, Ios.

> Important Note
> When creating your first FireStore instance you would be asked to chooses FireStore mode (mentioned earlier).
> This choice is a permanent one for the entire Cloud Project.

**Cloud FireStore Hierarchy**:
- Inside root you can create collections.
- Inside collections you can create documents. All documents always belong to 1 collection
- Inside documents you can again create a nested collection.
- Inside the nested collection you can again create new documents.
- The nested collections are specific to the document, each document gets its own nested collection.
- Example of Hierarchial Structure: root / collection1 / document1 / collection1_1 / document2



## Cloud BigTable
Cloud BigTable is a wide column, NoSql database. It is can scale up to PB, and is recommend for time-series data.

**Cloud BigTable Features**:
- H-Base compatible
- Petabyte scale, No-Sql database
- Designed for high volumes of analytical & operational data.
- Supports horizontal scaling with multiple nodes. Can handle millions of read/writes transactions per second at low latency.
- Does NOT support serverless.
- Data Export is not available in Google Cloud Console or gcloud CLI.
- Ability to export data available via Java Application or H-Base commands.
- Interacting with Cloud BigTable uses `cbt` command.



## Cloud MemoryStore
Cloud MemoryStore is a fully managed key-value database.

**Cloud MemoryStore Features**:
- Fully managed, highly available in memory database.
- Supports Redis and Memcache.

MemCache is recommend for cache purposes, otherwise use Redis.s



## Cloud BigQuery

<!-- TODO - BigQuery + Features -->
