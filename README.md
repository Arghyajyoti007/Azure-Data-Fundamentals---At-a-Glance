# Introduction to Microsoft Azure Data core data concepts

### Explore core data concepts
#### Identify data formats
You can classify data as structured, semi-structured, or unstructured.

**Structured data**  
Structured data is data that adheres to a fixed schema, so all of the data has the same fields or properties. Most commonly, the schema for structured data entities is tabular.  
Structured data is often stored in a database in which multiple tables can reference one another by using key values in a relational model.

**Semi-structured data**  
Semi-structured data is information that has some structure, but which allows for some variation between entity instances. One common format for semi-structured data is JavaScript Object Notation (JSON).

**Unstructured data**  
Not all data is structured or even semi-structured. For example, documents, images, audio and video data, and binary files might not have a specific structure. This kind of data is referred to as unstructured data.  

Organizations are also increasingly working with vector data (also called embeddings)—the data type that enables AI assistants to answer questions over your own documents and data.

#### Data Store
There are two broad categories of data store in common use:
- File stores
- Databases

### Explore file storage
The specific file format used to store data depends on many factors, including:
- The type of data being stored (structured, semi-structured, or unstructured).
- The applications and services that need to read, write, and process the data.
- The need for the data files to be readable by humans, or optimized for efficient storage and processing.

**Delimited text files**  
Data is often stored in plain text format with specific field delimiters and row terminators. The most common format for delimited data is comma-separated values (CSV).  

**JavaScript Object Notation (JSON)**  
JSON is a ubiquitous format in which a hierarchical document schema is used to define data entities (objects) that have multiple attributes.  

**Extensible Markup Language (XML)**  
XML uses tags enclosed in angle-brackets (<../>) to define elements and attributes.  

**Binary Large Object (BLOB)**  
Some file formats store the data as raw binary that must be interpreted by applications and rendered.  

**Optimized file formats**  
- **Parquet**: columnar format, de facto standard for lakehouses.  
- **Avro**: row-based format with JSON header and binary blocks.  
- **Delta Lake**: builds on Parquet with ACID transactions and versioning.

### Explore databases
**Relational databases**  
Used to store and query structured data in tables with primary keys and relationships.  

**Nonrelational databases (NoSQL)**  
Four common types:  
- Key-value databases  
- Document databases (JSON documents)  
- Column family databases  
- Graph databases  

### Explore transactional data processing
**OLTP (Online Transactional Processing)**  
Fast processing and frequent read/write operations. CRUD workloads.  

**ACID properties**  
- Atomicity  
- Consistency  
- Isolation  
- Durability  

OLTP systems support live applications (line of business apps).

### Explore analytical data processing
Analytical systems store historical data and metrics, optimized for read-heavy workloads.

**Common architecture**  
1. ETL/ELT into a data lake.  
2. Data loaded into tables in lakehouse/warehouse.  
3. Aggregated into OLAP/semantic models.  
4. Queried for reports, dashboards, visualizations.  

**Data lakes** → file-based, large-scale analytics.  
**Data warehouses** → relational schema optimized for queries.  
**Data lakehouses** → combine lake flexibility with warehouse querying.  

**Modern analytics platforms**  
- Microsoft Fabric: unified SaaS analytics.  
- Azure Databricks: large-scale engineering/science with Delta Lake.  
- Microsoft Purview: governance and compliance.  

**Medallion architecture**  
- Bronze: raw data.  
- Silver: cleansed/conformed data.  
- Gold: aggregated, business-ready data.

## Explore Data Roles and Services

### Job Roles in the World of Data
- **Database Administrators**  
  Manage databases, assign permissions, store backups, and restore data in case of failure.

- **Data Engineers**  
  Manage infrastructure and processes for data integration, apply data cleaning routines, define governance rules, and implement pipelines.

- **Data Analysts**  
  Explore and analyze data, create visualizations and charts, and enable informed decision-making.

- **AI Engineers**  
  Build and integrate AI-powered features, work with large language models, ML pipelines, and data sources for intelligent scenarios.

---

### Identify Data Services

#### Azure SQL
- **Azure SQL Database** – Fully managed PaaS database hosted in Azure.  
- **Azure SQL Managed Instance** – Hosted SQL Server instance with automated maintenance and flexible configuration.  
- **Azure SQL VM** – SQL Server installed on a VM, offering maximum configurability with full management responsibility.

#### Open-source Databases in Azure
- **Azure Database for MySQL** – Commonly used in LAMP stack apps.  
- **Azure Database for PostgreSQL** – Hybrid relational-object database supporting custom data types.

#### Azure Cosmos DB
- Global-scale NoSQL database supporting JSON, key-value, column-family, and graph data models.

#### Azure Storage
- **Blob Containers** – Scalable storage for binary files.  
- **File Shares** – Network file shares for corporate use.  
- **Tables** – Key-value storage for fast read/write operations.

#### Azure Data Factory
- Define and schedule pipelines to transfer and transform data.

#### Microsoft Fabric
- Unified SaaS analytics platform combining data engineering, warehousing, real-time analytics, data science, and Power BI.  
- **Fabric IQ** – Unifies data across OneLake with consistent business meaning.

#### Power BI
- Business intelligence and visualization platform for interactive reports and dashboards.

#### Azure Databricks
- Cloud analytics platform built on Apache Spark, optimized for large-scale data engineering and lakehouse analytics.

#### Azure Stream Analytics
- Real-time stream processing engine for querying and transforming input streams.

#### Azure Data Explorer
- High-performance big data analytics platform for log and telemetry data.

#### Microsoft Purview
- Enterprise-wide data governance and discoverability with lineage tracking.

#### Microsoft Foundry
- Unified PaaS for enterprise AI operations, model building, and app development.

---

## Explore Fundamental Relational Data Concepts

### Relational Data
- **Table** = Core entity  
- **Row** = Instance  
- **Column** = Attribute (type enforced: integer, text, date, decimal)  
- **Null** = Empty value

### Normalization
- Separate each entity into its own table.  
- Separate attributes into columns.  
- Use **Primary Keys (PK)** to uniquely identify rows.  
- Use **Foreign Keys (FK)** to link related entities.  
- Composite keys can be defined using multiple columns.

---

### SQL (Structured Query Language)

#### Dialects
- **T-SQL** – Microsoft SQL Server, Azure SQL Database, Managed Instance, SQL Server on VMs.  
- **pgSQL** – PostgreSQL dialect.  
- **PL/SQL** – Oracle’s Procedural Language/SQL.

#### SQL Statement Groups
- **DDL (Data Definition Language)**  
  - `CREATE`, `ALTER`, `DROP`, `RENAME`  
- **DCL (Data Control Language)**  
  - `GRANT`, `REVOKE`, `DENY`  
- **DML (Data Manipulation Language)**  
  - `SELECT`, `INSERT`, `UPDATE`, `DELETE`

---

### Database Objects

#### Views
Virtual tables based on SELECT queries.  
```sql
CREATE VIEW Deliveries AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.Customer = c.ID;
```
