# Explore Core Data Concepts

## Explore Core Data Concepts

### Identify Data Formats
You can classify data as structured, semi-structured, or unstructured [cite: 1]:

* **Structured data**: Adheres to a fixed schema where all records share identical fields and properties, most commonly arranged in tabular format [cite: 1]. It is frequently stored in relational databases using primary and foreign keys to relate tables [cite: 1].
* **Semi-structured data**: Contains organizational markers and internal structure but accommodates variation between instances (for example, JSON format) [cite: 1].
* **Unstructured data**: Lacks a predefined conceptual structure or schema (such as media files, audio, video, raw binary files, and documents) [cite: 1].
* **Vector data (embeddings)**: Specialized data representations used by AI assistants and LLMs to ground semantic searches across unstructured organizational documents [cite: 1].

**Data Stores**:
* **File stores**: File-based storage solutions optimized for raw or formatted file objects [cite: 1].
* **Databases**: Managed repositories optimized for relational or specialized record access [cite: 1].

### Explore File Storage
Storage format selection is driven by data structure, reader/writer application requirements, and the tradeoff between human readability and machine efficiency [cite: 1].

* **Delimited text files**: Plain text data organized with field delimiters (commas in CSV) and row terminators (carriage returns/newlines) [cite: 1]. Highly portable and human-readable [cite: 1].
* **JavaScript Object Notation (JSON)**: Hierarchical document schema supporting nested attributes and collections of objects [cite: 1].
* **Extensible Markup Language (XML)**: Tag-based hierarchical format enclosed in `<../>` brackets; widely used historically, though largely superseded by JSON [cite: 1].
* **Binary Large Object (BLOB)**: Unstructured raw binary streams (such as images, video, audio, and compiled artifacts) [cite: 1].
* **Parquet**: Columnar, compressed file format optimized for modern data lakehouses; groups column values together within row groups for efficient read filtering [cite: 1].
* **Avro**: Row-based binary storage format with an embedded JSON schema header, ideal for high-throughput write/streaming pipelines [cite: 1].
* **Delta Lake**: Open-source storage layer built on Parquet files coupled with a file-based transaction log, enabling ACID transactions, time travel/versioning, and schema enforcement [cite: 1].

### Explore Databases
* **Relational databases**: Store normalized data across structured tables with enforced schemas and unique primary keys, linked via foreign keys to eliminate redundant data values [cite: 1].
* **Non-relational (NoSQL) databases**: Non-tabular databases optimized for scale and flexible schema patterns [cite: 1]:
  * **Key-value stores**: Store pairs of unique keys mapped to arbitrary data values [cite: 1].
  * **Document stores**: Key-value variants where values are structured documents (typically JSON) accessible via query engines [cite: 1].
  * **Column-family stores**: Store tabular rows partitioned into logical column groupings [cite: 1].
  * **Graph stores**: Store entities as nodes and associations as edges to model complex interconnected networks [cite: 1].

### Explore Transactional Data Processing
* **Online Transactional Processing (OLTP)**: Optimizes concurrent read and write operations for low-latency line-of-business (LOB) applications handling transactional CRUD workflows [cite: 1].
* **ACID Guarantees**:
  * **Atomicity**: Transactions succeed completely or fail completely as a single unit [cite: 1].
  * **Consistency**: State changes strictly preserve data integrity and valid constraints [cite: 1].
  * **Isolation**: Concurrent transactions execute without mutual interference [cite: 1].
  * **Durability**: Committed data survives system failures permanently [cite: 1].

### Explore Analytical Data Processing
Read-optimized architectures that process large historical datasets to drive organizational insights and reporting [cite: 1].

* **Enterprise Analytics Pipeline**:
  1. Extract, Transform, and Load (ETL) or Extract, Load, and Transform (ELT) moves operational data into data lakes [cite: 1].
  2. Data is modeled into tables within data lakehouses or relational data warehouses [cite: 1].
  3. Data warehouse facts and dimensions feed OLAP / semantic models (such as Power BI semantic models) to pre-calculate business metrics [cite: 1].
  4. Reporting layers, dashboards, and visualization engines query these analytical layers [cite: 1].
* **Data Lakes**: Scalable repositories holding massive volumes of raw, multi-format files [cite: 1].
* **Data Warehouses**: Relational, schema-enforced stores optimized for read-heavy analytical SQL queries [cite: 1].
* **Data Lakehouses**: Hybrid architectures marrying flexible data lake object storage with transactional reliability and relational query optimizations [cite: 1].
* **Modern Analytics Platforms**:
  * **Microsoft Fabric**: SaaS analytics platform unifying OneLake storage, data engineering, data warehousing, and Power BI [cite: 1].
  * **Azure Databricks**: Apache Spark-based cloud analytics platform natively integrated with Delta Lake [cite: 1].
  * **Microsoft Purview**: Centralized governance, automated data cataloging, and end-to-end lineage tracking [cite: 1].
* **Medallion Lakehouse Architecture**:
  * **Bronze**: Raw, untransformed data ingested directly from source systems [cite: 1].
  * **Silver**: Cleaned, filtered, deduplicated, and conformed data [cite: 1].
  * **Gold**: Curated, business-level aggregated datasets ready for BI reporting [cite: 1].

## Explore Data Roles and Services

### Explore Job Roles in the World of Data
* **Database Administrator (DBA)**: Manages database infrastructure, user permissions, backups, high availability, and recovery [cite: 1].
* **Data Engineer**: Designs and implements ingestion pipelines, data transformation routines, governance policies, and storage architectures [cite: 1].
* **Data Analyst**: Evaluates, aggregates, and visualizes data using interactive reports and dashboards to guide business strategies [cite: 1].
* **AI Engineer**: Implements and operationalizes machine learning models, LLM workflows, and intelligent cognitive capabilities [cite: 1].

### Identify Data Services
* **Azure SQL Family**:
  * **Azure SQL Database**: Fully managed PaaS database with serverless and auto-scaling compute [cite: 1].
  * **Azure SQL Managed Instance**: PaaS offering providing near-100% on-premises SQL Server engine compatibility [cite: 1].
  * **SQL Server on Azure VMs**: IaaS deployment granting full OS and administrative control for lift-and-shift operations [cite: 1].
* **Open-Source Relational Databases**:
  * **Azure Database for MySQL**: Fully managed MySQL database engine commonly utilized in LAMP stacks [cite: 1].
  * **Azure Database for PostgreSQL**: Fully managed object-relational database with extensibility for custom and non-relational types [cite: 1].
* **Azure Cosmos DB**: Globally distributed NoSQL and multi-model database engine supporting sub-10ms response latencies [cite: 1].
* **Azure Storage**:
  * **Blob Containers**: Scalable object storage for raw unstructured data [cite: 1].
  * **File Shares**: Managed cloud SMB and NFS file shares [cite: 1].
  * **Tables**: Low-cost NoSQL key-value store [cite: 1].
* **Azure Data Factory**: Cloud-scale data integration service to orchestrate data-driven ETL/ELT pipelines [cite: 1].
* **Microsoft Fabric**: Comprehensive SaaS analytics environment encompassing OneLake, data warehousing, and Power BI [cite: 1].
* **Microsoft Fabric IQ**: Workload inside Microsoft Fabric providing unified business context and metadata across OneLake [cite: 1].
* **Power BI**: Enterprise business intelligence tool for interactive data visualization and enterprise reporting [cite: 1].
* **Azure Stream Analytics**: Managed stream processing engine for real-time complex event processing and analytics [cite: 1].
* **Azure Data Explorer**: High-speed, low-latency analytics service optimized for time-series logs and telemetry [cite: 1].
* **Microsoft Foundry**: Unified enterprise PaaS environment for generative AI engineering and model operationalization [cite: 1].

---

# Explore Relational Data in Azure

## Explore Fundamental Relational Data Concepts

### Understand Relational Data
* **Table**: Core entity representing a collection of related records [cite: 1].
* **Row (Tuple / Record)**: An individual instance of an entity [cite: 1].
* **Column (Attribute)**: A discrete field holding a specific, enforced data type (Integer, Varchar, Date, Decimal) [cite: 1].
* **NULL**: Denotes an absence of recorded data or unknown value within a field [cite: 1].

### Understand Normalization
Database design process intended to eliminate redundancy and improve data integrity [cite: 1]:
* Isolates entities into separate dedicated tables [cite: 1].
* Separates discrete attributes into independent columns [cite: 1].
* Assigns unique **Primary Keys (PK)** to each row instance [cite: 1].
* Establishes relationships across tables using **Foreign Keys (FK)** [cite: 1].
* Accommodates **Composite Keys** combining two or more attributes to ensure uniqueness [cite: 1].

### Explore SQL (Structured Query Language)
* **SQL Dialects**:
  * **T-SQL**: Proprietary procedural dialect used by Microsoft SQL Server and Azure SQL [cite: 1].
  * **pgSQL**: Dialect used by PostgreSQL [cite: 1].
  * **PL/SQL**: Procedural language extension utilized by Oracle [cite: 1].
* **Command Categorization**:
  * **DDL (Data Definition Language)**: Defines schema structure (`CREATE`, `ALTER`, `DROP`, `RENAME`) [cite: 1].
  * **DCL (Data Control Language)**: Manages permissions and security boundaries (`GRANT`, `REVOKE`, `DENY`) [cite: 1].
  * **DML (Data Manipulation Language)**: Manages row data manipulation (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) [cite: 1].

### Describe Database Objects
* **Views**: Virtual tables representing predefined queries, simplifying access to complex joins:
  ```sql
  CREATE VIEW Deliveries
  AS
  SELECT o.OrderNo, o.OrderDate,
         c.FirstName, c.LastName, c.Address, c.City
  FROM Order AS o JOIN Customer AS c
  ON o.Customer = c.ID;
  ```
  [cite: 1]
* **Stored Procedures**: Pre-compiled batches of SQL statements and programmatic logic accepting parameters to standardize routines and enforce security:
  ```sql
  CREATE PROCEDURE RenameProduct
      @ProductID INT,
      @NewName VARCHAR(20)
  AS
  UPDATE Product
  SET Name = @NewName
  WHERE ID = @ProductID;
  ```
  [cite: 1]
* **Indexes**: Specialized lookup data structures that significantly accelerate retrieval performance, offset by computational overhead and storage requirements during write operations:
  ```sql
  CREATE INDEX idx_ProductName
  ON Product(Name);
  ```
  [cite: 1]

## Explore Relational Database Services in Azure

### Describe Azure SQL Services and Capabilities
* **SQL Server on Azure Virtual Machines (VMs)**: IaaS offering delivering operating-system-level access for legacy migrations and custom software integrations [cite: 1].
* **Azure SQL Managed Instance**: Fully managed PaaS supporting native virtual networking, cross-database querying, and SQL Agent jobs with automated patch management [cite: 1].
* **Azure SQL Database**: Fully managed, cloud-native PaaS database featuring serverless compute scaling and elastic pool resource allocation [cite: 1].

---

# Explore Non-Relational Data in Azure

## Explore Azure Storage for Non-Relational Data

### Explore Azure Blob Storage
Cloud-based object store designed for massive volumes of unstructured binary data grouped into containers [cite: 1].
* **Blob Specialized Types**:
  * **Block Blobs**: Managed in blocks up to 4,000 MiB (up to ~190.7 TiB total capacity), ideal for static files and documents [cite: 1].
  * **Page Blobs**: Composed of 512-byte pages supporting random read/write access (up to 8 TB capacity), backing Azure Virtual Machine virtual disks (VHDs) [cite: 1].
  * **Append Blobs**: Tailored exclusively for append-only operations (up to 195 GB capacity), ideal for real-time activity and diagnostics logging [cite: 1].
* **Access Tiers**:
  * **Hot Tier**: Optimized for high-frequency read and write access on high-performance media [cite: 1].
  * **Cool Tier**: Low storage costs balanced by higher access fees; requires a 30-day minimum retention period [cite: 1].
  * **Cold Tier**: Infrequently modified or accessed assets; requires a 90-day minimum retention period [cite: 1].
  * **Archive Tier**: Lowest storage pricing with offline storage; retrieval requires rehydration taking up to 15 hours, with a 180-day minimum retention period [cite: 1].
* **Lifecycle Management**: Automated rules to transition blobs between access tiers or trigger deletion based on last-modified timestamps [cite: 1].
* **Data Redundancy Strategies**:
  * **LRS (Locally Redundant Storage)**: Three synchronous copies within a single datacenter facility [cite: 1].
  * **ZRS (Zone-Redundant Storage)**: Synchronously replicated across three distinct physical availability zones in the primary region [cite: 1].
  * **GRS / GZRS (Geo-Redundant / Geo-Zone-Redundant Storage)**: Replicated asynchronously to a secondary paired geographical region [cite: 1].
  * **RA-GRS / RA-GZRS**: Provides direct read capabilities to secondary region replicas prior to failover [cite: 1].

### Explore Azure Data Lake Storage Gen2
* Enterprise data lake engine combining Blob Storage cost efficiency with a Hierarchical Namespace (HFS) [cite: 1].
* Translates directory structures into true file system operations and enables POSIX-compliant Access Control Lists (ACLs) [cite: 1].
* Serves as underlying storage for Azure Databricks mounts and Microsoft Fabric OneLake [cite: 1].
* Upgrading an Azure Storage account to enable Hierarchical Namespace is a one-way, irreversible operation [cite: 1].

### Explore Microsoft OneLake in Fabric
* **Organization-Wide Data Lake**: Single unified SaaS logical data lake provisioning automatically with each Microsoft Fabric tenant [cite: 1].
* **Distributed Ownership**: Governed workspaces facilitate departmental self-service without creating fragmented data silos [cite: 1].
* **Delta-Parquet Format**: Native support for open Delta Lake Parquet standards coupled with direct ADLS Gen2 API compatibility [cite: 1].
* **Client Integration**: Direct desktop access via OneLake File Explorer on Windows [cite: 1].

### Explore Azure Files
* Managed cloud-hosted network file shares accessible through standard protocols, offering capacities up to 256 TiB with 4 TiB file maximums [cite: 1].
* Supports hybrid synchronization through the **Azure File Sync** agent [cite: 1].
* **Supported Protocols**:
  * **SMB (Server Message Block)**: Multi-platform access supported across Windows, macOS, and Linux [cite: 1].
  * **NFS (Network File System)**: Linux-specific protocol requiring SSD premium tier storage and configured virtual networks [cite: 1].

### Explore Azure Tables
* Schemaless NoSQL key-value store maintaining denormalized tables [cite: 1].
* **Azure Cosmos DB for Table**: Premium service upgrade offering higher throughput, millisecond latencies, and global replication [cite: 1].
* **Partitioning Scheme**:
  * **PartitionKey**: Groups related entities onto identical physical partitions to optimize parallel scale and I/O efficiency [cite: 1].
  * **RowKey**: Unique identifier for an entity within a given partition [cite: 1].
  * **Composite Identification**: Queries targeting both `PartitionKey` and `RowKey` enable high-speed point lookups and range scans [cite: 1].

## Explore Fundamentals of Azure Cosmos DB

### Describe Azure Cosmos DB
* Fully managed NoSQL Platform-as-a-Service (PaaS) database providing schema-agnostic storage and automatic property indexing.
* Global multi-master replication guarantees sub-10ms response latencies at the 99th percentile.
* **Resource Hierarchy**:
  * **Account**: Root Azure resource containing one or more databases.
  * **Database**: Logical administrative grouping of containers.
  * **Container**: Primary unit of scalability, throughput allocation, indexing, and TTL (logical partitions scale up to 20 GB).
  * **Items**: Core data entities stored inside containers (documents, rows, or nodes/edges).
* **Configurable Consistency Levels**:
  * **Strong**: Linearizable consistency; reads consistently return the most recently committed write.
  * **Bounded Staleness**: Reads lag behind updates by a strictly defined time lag or update version threshold.
  * **Session**: Guaranteed monotonic reads and write-following-reads within an individual client session (industry standard default).
  * **Consistent Prefix**: Guarantees updates are never delivered out of sequence, though reads may be stale.
  * **Eventual**: Lowest latency and highest availability; replicas converge asynchronously over time.
* **Throughput Capacity & Modes**:
  * Measured in **Request Units per second (RU/s)**, where 1 RU/s correlates to reading a 1-KB document.
  * **Dedicated**: Throughput reserved for a specific container.
  * **Shared**: Throughput allocated across a database pool (up to 25 containers).
  * **Serverless**: On-demand billing model ideal for sporadic or unpredictable traffic patterns.
  * **Autoscale**: Dynamically scales RU/s between 10% and 100% of a configured maximum ceiling based on active load.

### Identify Azure Cosmos DB APIs
* **Cosmos DB for NoSQL**: Native JSON document API using SQL query syntax; supports native Microsoft Fabric mirroring without dedicated ETL pipelines.
* **Cosmos DB for MongoDB**: Wire-protocol compatible with MongoDB client drivers, storing data in BSON format and querying via MongoDB Query Language (MQL).
* **Cosmos DB for Table**: Key-value API supporting existing Azure Table Storage applications with global distribution and autoscale RU/s.
* **Cosmos DB for Apache Cassandra**: Wire-compatible with Apache Cassandra column-family tables.
* **Cosmos DB for Apache Gremlin**: Graph database API supporting vertices (nodes) and edges (relationships) for graph traversal queries.

---

# Explore Fundamentals of Real-Time Analytics

## Explore Fundamentals of Real-Time Analytics

### Understand Batch and Stream Processing
* **Batch Processing**:
  * Analyzes large volumes of accumulated historical data in periodic schedules [cite: 1].
  * High-latency processing window (minutes to hours) [cite: 1].
  * Optimized for computationally complex aggregations and comprehensive trend analysis [cite: 1].
* **Stream Processing**:
  * Analyzes real-time unbounded data streams continuously as events occur [cite: 1].
  * Low-latency processing window (seconds to milliseconds) [cite: 1].
  * Optimized for real-time alerting, time-windowed metrics, and simple aggregations [cite: 1].
* **Lambda Architecture**:
  * Hybrid data architecture combining a batch layer for historical accuracy with a speed/streaming layer for real-time insights [cite: 1].

### Explore Common Elements of Stream Processing Architecture
* **Source**: Event generation systems that produce raw data streams (such as IoT telemetry, application logs, and message queues) [cite: 1].
* **Processing**: Real-time compute engines (such as Azure Stream Analytics or Spark Streaming) that ingest, filter, and aggregate streaming events [cite: 1].
* **Sink**: Destination data stores or presentation layers (such as Azure Cosmos DB, Power BI dashboards, or cold-tier data lakes) [cite: 1].
