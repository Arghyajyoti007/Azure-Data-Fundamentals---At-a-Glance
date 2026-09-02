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
