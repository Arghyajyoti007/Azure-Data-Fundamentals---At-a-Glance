# Introduction to Microsoft Azure Data core data concepts 

## Explore core data concepts

### Identify data formats
You can classify data as structured, semi-structured, or unstructured.

#### Structured data
Structured data is data that adheres to a fixed schema, so all of the data has the same fields or properties. Most commonly, the schema for structured data entities is tabular.
Structured data is often stored in a database in which multiple tables can reference one another by using key values in a relational model.

#### Semi-structured data
Semi-structured data is information that has some structure, but which allows for some variation between entity instances. One common format for semi-structured data is JavaScript Object Notation (JSON).

#### Unstructured data
Not all data is structured or even semi-structured. For example, documents, images, audio and video data, and binary files might not have a specific structure. This kind of data is referred to as unstructured data.

Organizations are also increasingly working with vector data (also called embeddings)—the data type that enables AI assistants to answer questions over your own documents and data.

#### Data Store
There are two broad categories of data store in common use:
- **File stores**
- **Databases**

---

# Explore file storage
The specific file format used to store data depends on many factors, including:
- The type of data being stored (structured, semi-structured, or unstructured).
- The applications and services that need to read, write, and process the data.
- The need for the data files to be readable by humans, or optimized for efficient storage and processing.

### Delimited text files
Data is often stored in plain text format with specific field delimiters and row terminators. The most common format for delimited data is comma-separated values (CSV) in which fields are separated by commas, and rows are terminated by a carriage return / new line. Delimited text is a good choice for structured data that needs to be accessed by a wide range of applications and services in a human-readable format.

### JavaScript Object Notation (JSON)
JSON is a ubiquitous format in which a hierarchical document schema is used to define data entities (objects) that have multiple attributes. Each attribute might be an object (or a collection of objects).

### Extensible Markup Language (XML)
XML uses tags enclosed in angle-brackets (`<../>`) to define elements and attributes. It's largely been superseded by the less verbose JSON format, but there are still some systems that use XML to represent data.

### Binary Large Object (BLOB)
Some file formats however, particularly for unstructured data, store the data as raw binary that must be interpreted by applications and rendered. Common types of data stored as binary include images, video, audio, and application-specific documents.

### Optimized file formats
- **Parquet**: A columnar data format and the de facto standard for modern data lakehouses. It's an Apache project. A Parquet file contains row groups. Data for each column is stored together in the same row group. Each row group contains one or more chunks of data.
- **Avro**: A row-based format created by Apache. Each file contains a header that describes the structure of the data in the file. This header is stored as JSON. The data is stored as binary information in one or more blocks of records.
- **Delta Lake**: An open-source storage format that builds on Parquet by adding a transaction log, which enables ACID transactions, data versioning, and reliable updates on top of files stored in a data lake.

---

# Explore databases

### Relational databases
Relational databases are commonly used to store and query structured data. The data is stored in tables that represent entities, such as customers, products, or sales orders. Each instance of an entity is assigned a primary key that uniquely identifies it; and these keys are used to reference the entity instance in other tables. This use of keys to reference data entities enables a relational database to be normalized; which in part means the elimination of duplicate data values.

### Nonrelational databases
Nonrelational databases are often referred to as NoSQL databases, even though some support a variant of the SQL language.

There are four common types of nonrelational databases commonly in use:
1. **Key-value databases**: Each record consists of a unique key and an associated value, which can be in any format.
2. **Document databases**: A specific form of key-value database in which the value is a JSON document (which the system is optimized to parse and query).
3. **Column family databases**: Store tabular data comprising rows and columns, but you can divide the columns into groups known as column-families. Each column family holds a set of columns that are logically related together.
4. **Graph databases**: Store entities as nodes with links to define relationships between them.

---

# Explore transactional data processing

### OLTP - Online Transactional Processing
Fast processing and frequent read and write operations.
OLTP solutions rely on a database system in which data storage is optimized for both read and write operations in order to support transactional workloads in which data records are created, retrieved, updated, and deleted (often referred to as CRUD operations).

### ACID Properties
- **Atomicity**: Each transaction is treated as a single unit, which succeeds completely or fails completely.
- **Consistency**: Transactions can only take the data in the database from one valid state to another.
- **Isolation**: Concurrent transactions can't interfere with one another, and must result in a consistent database state.
- **Durability**: When a transaction has been committed, it will remain committed.

OLTP systems are typically used to support live applications that process business data - often referred to as line of business (LOB) applications.

---

# Explore analytical data processing

Analytical data processing typically uses read-only (or read-mostly) systems that store vast volumes of historical data or business metrics.

### Enterprise-scale analytics architecture:
1. Operational data is extracted, transformed, and loaded (ETL) into a data lake for analysis—or extracted and loaded first with transformations applied afterward, a pattern called ELT that's common in modern lakehouses.
2. Data is loaded into a schema of tables - typically in a data lakehouse with tabular abstractions over files in the data lake, or a data warehouse with a fully relational SQL engine.
3. Data in the data warehouse may be aggregated and loaded into an **Online Analytical Processing (OLAP) model—today more commonly called a semantic model (and historically a cube)**. Aggregated numeric values (measures) from fact tables are calculated for intersections of dimensions from dimension tables. For example, sales revenue might be totaled by date, customer, and product. Power BI semantic models are the most common example you'll meet.
4. The data in the data lake, data warehouse, and analytical model can be queried to produce reports, visualizations, and dashboards.

- **Data lakes**: Common in large-scale data analytical processing scenarios, where a large volume of file-based data must be collected and analyzed.
- **Data warehouses**: An established way to store data in a relational schema that's optimized for read operations – primarily queries to support reporting and data visualization.
- **Data Lakehouses**: A more recent innovation that combines the flexible and scalable storage of a data lake with the relational querying semantics of a data warehouse. The table schema may require some denormalization of data in an OLTP data source (introducing some duplication to make queries perform faster).

### Modern analytics platforms
- **Microsoft Fabric**: A unified software as a service (SaaS) analytics platform that brings storage, data engineering, data warehousing, and reporting capabilities together in a single workspace.
- **Azure Databricks**: A cloud analytics platform built for large-scale data engineering and data science, using Delta Lake—Parquet plus a transaction log that enables versioning and ACID transactions—as its standard storage format.
- **Microsoft Purview**: Provides unified data security, governance, and compliance, helping you discover, classify, protect, and manage data across all your data sources.

### Organizing data with the medallion architecture
A common pattern for organizing data in a lakehouse is the medallion architecture, which uses three layers:
- **Bronze**: Raw data ingested as-is from source systems, with no transformations applied, preserving the original records for reprocessing.
- **Silver**: Cleansed and conformed data, with duplicates removed and data types standardized.
- **Gold**: Aggregated, business-ready data modeled for specific reporting and analytics use cases.

---

## Explore data roles and services

### Explore job roles in the world of data
The key job roles that deal with data in most organizations are:
- **Database administrators**: Manage databases, assigning permissions to users, storing backup copies of data, and restoring data in the event of a failure.
- **Data engineers**: Manage infrastructure and processes for data integration across the organization, applying data cleaning routines, identifying data governance rules, and implementing pipelines to transfer and transform data between systems.
- **Data analysts**: Explore and analyze data to create visualizations and charts that enable organizations to make informed decisions.
- **AI engineers**: Build and integrate AI-powered features and workflows, working with large language models, machine learning pipelines, and data sources to enable intelligent scenarios.

### Identify data services
- **Azure SQL**: The collective name for a family of relational database solutions based on the Microsoft SQL Server database engine.
  - **Azure SQL Database**: A fully managed platform-as-a-service (PaaS) database hosted in Azure.
  - **Azure SQL Managed Instance**: A hosted instance of SQL Server with automated maintenance, which allows more flexible configuration than Azure SQL DB but with more administrative responsibility for the owner.
  - **Azure SQL VM**: A virtual machine with an installation of SQL Server, allowing maximum configurability with full management responsibility.
- **Open-source databases in Azure**:
  - **Azure Database for MySQL**: A simple-to-use open-source database management system commonly used in LAMP stack apps.
  - **Azure Database for PostgreSQL**: A hybrid relational-object database supporting custom data types and nonrelational properties.
- **Azure Cosmos DB**: A global-scale nonrelational (NoSQL) database system that supports multiple APIs (JSON documents, key-value pairs, column-families, graphs).
- **Azure Storage**:
  - **Blob containers**: Scalable, cost-effective storage for binary files.
  - **File shares**: Network file shares as typically found in corporate networks.
  - **Tables**: Key-value storage for applications requiring fast reads and writes.
- **Azure Data Factory**: Define and schedule data pipelines to transfer and transform data.
- **Microsoft Fabric**: Microsoft's unified SaaS analytics platform bringing data engineering, data warehousing, real-time analytics, data science, and Power BI together on top of OneLake.
- **Microsoft Fabric IQ**: Workload in Microsoft Fabric that unifies data across OneLake and gives it consistent business meaning.
- **Power BI**: Business intelligence and data visualization platform for interactive reports and dashboards.
- **Azure Databricks**: Cloud analytics platform built on Apache Spark for data engineering, data science, and SQL analytics over Delta Lake.
- **Azure Stream Analytics**: Real-time stream processing engine capturing streaming data, transforming via queries, and outputting for processing/storage.
- **Azure Data Explorer**: Fully managed, high-performance big data analytics platform for log and telemetry data.
- **Microsoft Purview**: Enterprise-wide data governance, discoverability, data mapping, and lineage tracking.
- **Microsoft Foundry**: Microsoft's unified Azure PaaS for enterprise AI operations, model builders, and application development.

---

## Explore fundamental relational data concepts

### Understand relational data
- **Table** = Core Entity
- **Row** = Instance
- **Column** = Attribute
- **Type enforcement**: Each column stores data of a specific datatype (Integer, Variable Length Text, Date, Decimal Numeric, etc.). Empty fields represent `NULL`.

### Understand normalization
- Separate Instance, Separate Attribute, Primary Key (PK), and Foreign Key (FK).
- Separate each entity into its own table.
- Separate each discrete attribute into its own column.
- Uniquely identify each entity instance (row) using a primary key.
- Use foreign key columns to link related entities.
- A key (primary or foreign) can be defined as a composite key based on a unique combination of multiple columns.

### Explore SQL (Structured Query Language)
Some popular dialects of SQL include:
- **Transact-SQL (T-SQL)**: Microsoft SQL Server, Azure SQL Database, Azure SQL Managed Instance, and SQL Server on Azure VMs.
- **pgSQL**: Dialect with extensions implemented in PostgreSQL.
- **PL/SQL**: Oracle's Procedural Language/SQL.

SQL statements are grouped into three main logical groups:
1. **DDL (Data Definition Language)**:
   - `CREATE`: Create a new object in the database (table, view, etc.).
   - `ALTER`: Modify the structure of an object.
   - `DROP`: Remove an object from the database.
   - `RENAME`: Rename an existing object.
2. **DCL (Data Control Language)**:
   - `GRANT`: Grant access to perform specific actions.
   - `REVOKE`: Revoke previously granted permissions.
   - `DENY`: Deny access to perform specific actions.
3. **DML (Data Manipulation Language)**:
   - `SELECT`: Read data.
   - `INSERT`: Insert data into a table.
   - `UPDATE`: Modify data in existing rows (use `WHERE` clause).
   - `DELETE`: Delete table records (use `WHERE` clause).

### Describe database objects
- **Views**: A virtual table based on the results of a SELECT query. Store queries that are used frequently.
  ```sql
  CREATE VIEW Deliveries
  AS
  SELECT o.OrderNo, o.OrderDate,
         c.FirstName, c.LastName, c.Address, c.City
  FROM Order AS o JOIN Customer AS c
  ON o.Customer = c.ID;
  ```
- **Stored Procedures**: Encapsulate programmatic logic by name, callable when required, supporting parameters and improving security.
  ```sql
  CREATE PROCEDURE RenameProduct
      @ProductID INT,
      @NewName VARCHAR(20)
  AS
  UPDATE Product
  SET Name = @NewName
  WHERE ID = @ProductID;
  ```
- **Indexes**: Improve read query speeds with a tradeoff in storage space and maintenance overhead on writes (insert, update, delete).
  ```sql
  CREATE INDEX idx_ProductName
  ON Product(Name);
  ```

### Explore relational database services in Azure
- **SQL Server on Azure Virtual Machines (VMs)**: IaaS solution providing complete SQL Server control for lift-and-shift migrations.
- **Azure SQL Managed Instance**: PaaS solution offering near-100% compatibility with on-premises SQL Server instances with automated patching and backups.
- **Azure SQL Database**: Fully managed, cloud-native PaaS database for modern cloud applications.

---

# Introduction to Microsoft Azure Data non-relational data in Azure

## Explore Azure Storage for nonrelational data

### Explore Azure blob storage
Azure Blob Storage enables storing massive amounts of unstructured binary large objects in containers with container-level access control.

#### Blob Types:
- **Block blobs**: Handled as sets of blocks up to 4,000 MiB each (up to ~190.7 TiB total). Best for discrete, large objects that change infrequently (e.g., images).
- **Page blobs**: Organized as 512-byte pages (up to 8 TB). Optimized for random read/write; used for VM virtual disks.
- **Append blobs**: Optimized for append-only operations (up to 4 MB per block, ~195 GB total).

#### Access Tiers:
- **Hot tier**: Default, high-performance media for frequently accessed data.
- **Cool tier**: Lower storage cost, higher access cost; minimum 30-day retention to avoid early deletion charges.
- **Cold tier**: Rarely accessed/modified, fast retrieval; minimum 90-day retention.
- **Archive tier**: Lowest storage cost, offline state with high latency (up to 15 hours rehydration latency); minimum 180-day retention.

Lifecycle management policies automate movement across tiers based on age or rule definitions, as well as automatic deletion.

#### Redundancy Options:
- **LRS (Locally redundant storage)**: 3 copies within a single datacenter.
- **ZRS (Zone-redundant storage)**: 3 availability zones in the primary region.
- **GRS / GZRS (Geo-redundant / Geo-zone-redundant storage)**: Replicated asynchronously to a secondary region.
- **RA-GRS / RA-GZRS**: Read-access enabled to the secondary region.

### Explore Azure Data Lake Storage Gen2
- Combines Blob Storage scalability and cost-efficiency with a hierarchical file system (HFS).
- Compatible with Apache Spark, Azure Databricks, and Microsoft Fabric OneLake.
- POSIX-compliant Access Control Lists (ACLs) for granular file/folder permissions.
- Enabled via Hierarchical Namespace on storage accounts (one-way upgrade).

### Explore Microsoft OneLake in Fabric
Microsoft Fabric automatically provisions OneLake, built upon Azure Data Lake Storage Gen2.
- **Organization-wide data lake**: Single logical data lake per tenant.
- **Distributed ownership**: Workspaces allow teams to manage data while maintaining unified governance.
- **Open and compatible**: Delta Parquet format natively supported with ADLS Gen2 APIs.
- **Easy navigation**: Access via OneLake File Explorer on Windows.

### Explore Azure Files
- Managed cloud file shares accessible via industry-standard protocols.
- Scalable up to 256 TiB per share (SSD) with up to 4 TiB individual file sizes and 2,000 concurrent handles.
- **Tiers**: HDD and SSD media tiers.
- **Protocols**:
  - **SMB (Server Message Block)**: Multi-platform (Windows, Linux, macOS).
  - **NFS (Network File System)**: Linux-only (kernel 4.3+), requires SSD tier and VNet configuration.

### Explore Azure Tables
- NoSQL key-value store using tables and rows without fixed schema (except keys and timestamp).
- **Azure Cosmos DB for Table**: Premium service alternative offering higher throughput and global distribution.
- **Key Structure**:
  - **PartitionKey**: Groups related rows, determines physical partition for scalability and query scoping.
  - **RowKey**: Unique identifier within a partition.
- Supports rapid point queries and range queries within partitions.

# Explore fundamentals of Azure Cosmos DB

## Describe Azure Cosmos DB

Azure Cosmos DB is a fully managed NoSQL database service on Azure—a platform-as-a-service (PaaS) offering. Microsoft handles all of the underlying infrastructure: server provisioning, patching, updates, and backups. You focus on your application logic while Cosmos DB handles the operational overhead.

Cosmos DB is schema-agnostic. Items stored in the same container don't need to share the same structure. 

Microsoft uses Cosmos DB internally for some of its most demanding services, including Xbox Live, Microsoft 365, and core parts of Azure.

Cosmos DB uses a four-level resource hierarchy to organize your data:
* **Account**: The top-level Azure resource. A single account can contain unlimited databases.
* **Database**: A logical namespace that groups related containers together.
* **Container**: The primary unit of storage and scaling. You configure the partition key, throughput, indexing policy, and an optional time-to-live (TTL) at the container level.
* **Items**: Individual data entities stored inside a container. Depending on which API you use, items may be called documents, rows, nodes, or edges.

The partition key is a property you choose to distribute data across logical partitions. Each logical partition can hold up to 20 GB of data. 

Cosmos DB automatically creates and maintains indexes on all item properties by default.

Cosmos DB is built for global distribution. Add Azure regions to your account at any time, and the service automatically replicates your data to each one. Multi-region write accounts provide high availability guarantees. At the 99th percentile, reads typically complete in around 4 milliseconds and writes in around 5 milliseconds.

Cosmos DB offers five consistency levels so you can tune that trade-off:

| Consistency Level | Description |
| :--- | :--- |
| **Strong** | Every read reflects the most recent write. |
| **Bounded staleness** | Reads lag behind writes by a configurable interval (time or version count). |
| **Session** | Consistency is guaranteed within a single client session. This is the most widely used level. |
| **Consistent prefix** | Reads never see out-of-order writes but may see stale data. |
| **Eventual** | Replicas converge over time; the weakest guarantee but the highest availability. |

Cosmos DB measures capacity in Request Units per second (RU/s). One RU/s roughly equals the cost of reading a 1-KB item.

Three throughput modes are available:

| Mode | Description |
| :--- | :--- |
| **Dedicated** | Throughput is reserved exclusively for a single container. |
| **Shared** | Throughput is provisioned at the database level and shared across up to 25 containers. |
| **Serverless** | No throughput to provision upfront; you pay per request. Best for workloads with unpredictable or low traffic. |

The autoscale option lets you set a maximum RU/s, and Cosmos DB adjusts capacity automatically within that range based on actual demand.

Cosmos DB is a strong fit for applications that need flexible schema, global reach, and consistent low latency:
* **IoT and telemetry**: Fast ingestion of high-frequency device data, available for near-real-time processing.
* **Gaming**: Player profiles, leaderboards, and in-game stats that require single-digit millisecond response times.
* **Retail and e-commerce**: Product catalogs, shopping carts, and order pipelines at any scale.
* **Web and mobile apps**: Personalized user experiences, social features, and third-party integrations.

Some workloads aren't a good fit. If your application depends on complex multi-table joins, Azure SQL Database is better suited. For large-scale historical analytics, consider Microsoft Fabric or Azure Synapse Analytics instead.
