A data warehouse is a centralized repository that stores integrated data from multiple sources, designed for query and analysis.
it is use to support decision-making processes by providing a comprehensive view of the organization's data.

Benefits of Data Warehousing
---
- Improved Data Quality and Consistency
- Enhanced Business Intelligence and Reporting
- Faster Query Performance
- Historical Data Analysis

Challenges in Data Warehousing
---
- Data Integration Issues
- High Implementation Costs
- Complex ETL Processes
- Data Security and Privacy

Popular Data Warehousing Tools
---
- Amazon Redshift
- Google BigQuery
- Snowflake
- Microsoft Azure Synaps

Characteristics of Data Warehouses
---
- Subject-Oriented: Organized around key subjects like sales, finance, etc.
- Integrated: Combines data from various sources into a unified format.
- Time-Variant: Stores historical data for trend analysis.
- Non-Volatile: Data is stable and not frequently changed

Data Warehousing Architecture
----
- Bottom Tier: Data Sources (Operational Databases, External Data Sources)
-  Middle Tier: Data Warehouse Server (ETL Processes, Data Integration)
- Top Tier: Front-End Tools (Reporting, Data Analysis, OLAP)

# ETL Process

- Extraction: Pulling data from source systems.
- Transformation: Converting data into a usable format.
- Loading: Inserting transformed data into the data warehouse

- ETL Tools : Apache NiFi Talend Informatica

# Data Warehouse Schema

- A schema is a logical description of the entire database.
- It includes the definitions and relationships of tables, views, indexes, and other elements.
- Purpose: Organizes data in a way that supports efficient querying and analysis.

## Star Schema:
A type of database schema that organizes data into fact tables and dimension tables.

Structure:
    - Fact Table: Central table containing quantitative data (metrics/measures).
    - Dimension Tables: Surrounding tables containing descriptive attributes (dimensions).

## Snowflake Schema:
An extension of the star schema where dimension tables are normalized into multiple related tables.
Structure:
    - Fact Table: Central table with quantitative data.
    - Normalized Dimension Tables: Dimension tables broken down into additional related table

## Fact Constellation
Schema
- A complex schema that contains multiple fact tables sharing dimension tables, also known as a galaxy schema.
Structure:
    - Multiple Fact Tables: Central tables for different business processes.
    -  Shared Dimension Tables: Common dimension tables used by multiple fact tables

Data Warehousing Models
---
1. Operational Data Store( ODS):  Short-term data storage for daily operations.
2. Data Mart: Subset of data warehouse focused on a specific business area.
3. Enterprise Data Warehouse (EDW): Central repository of all data in an organization.

Data Warehousing Trends
---
- Cloud Data Warehousing
- Real-Time Data Warehousing
- Data Lakes and Lakehouses
- AI and Machine Learning Integration

Best Practices
---
Data Quality Management -> Scalability and Performance Optimization ->  Regular Backups and Recovery Plans -> User Training and Support

# OLAP and OLTP
## OLAP

OLAP is a category of software tools that provide analysis of data stored in a database.
Purpose: To support complex queries and data analysis, enabling decision-making processes

OLAP stands for Online Analytical Processing.
OLAP systems have the capability to analyze database information of multiple systems at the current time.
The primary goal of OLAP Service is data analysis and not data processing.

Online Analytical Processing (OLAP) consists of a type of software tool that is used for data analysis for business decisions.
OLAP provides an environment to get insights from the database retrieved from multiple database systems at one time.

Any type of Data Warehouse System is an OLAP system.
- Spotify analyzed songs by users to come up with a personalized homepage of their songs and playlist.
- Netflix movie recommendation system.

Benefits of OLAP Services
- OLAP services help in keeping consistency and calculation.
- We can store planning, analysis, and budgeting for business analytics within one platform.
- OLAP services help in handling large volumes of data, which helps in enterprise-level business applications.
- OLAP services help in applying security restrictions for data protection.
- OLAP services provide a multidimensional view of data, which helps in applying operations on data in various ways.

Drawbacks of OLAP Services
- OLAP Services requires professionals to handle the data because of its complex modeling procedure.
- OLAP services are expensive to implement and maintain in cases when datasets are large.
- We can perform an analysis of data only after extraction and transformation of data in the case of OLAP which delays the system.
- OLAP services are not efficient for decision-making, as it is updated on a periodic basis.


### OLAP Operations
-  Roll Up: Aggregate data by climbing up a concept hierarchy
- Drill Down: Move from summary data to more detailed data.
- Slice: Analyze data across a single dimension.
- Dice: Analyze data across multiple dimensions.
- Pivot: Reorient the multidimensional view of data.

### OLAP Architecture
- Multidimensional Databases (MOLAP): Data is stored in a multidimensional cube.
- Relational Databases (ROLAP): Data is stored in relational tables.
- Hybrid OLAP (HOLAP): Combines MOLAP and ROLAP approaches.

### OLAP Cube
- A data structure that allows fast analysis of data according to the multiple dimensions that define a business problem.
It has
- Dimensions: The perspectives or entities with respect to which an organization wants to keep records.
- Measures: The actual data values, often numeric, that are of interest.

----
## Online Transaction Processing (OLTP)
----
OLTP stands for Online Transaction Processing.
OLTP has the work to administer day-to-day transactions in any organization.
The main goal of OLTP is data processing not data analysis.

Online transaction processing provides transaction-oriented applications in a 3-tier architecture.
OLTP administers the day-to-day transactions of an organization.


An example considered for OLTP System is ATM Center

The uses of the OLTP System .
- ATM center is an OLTP application.

- OLTP handles the ACID properties during data transactions via the application.
- It’s also used for Online banking, Online airline ticket booking, sending a text message, add a book to the shopping cart.

Benefits of OLTP Services
- OLTP services allow users to read, write and delete data operations quickly.
- OLTP services help in increasing users and transactions which helps in real-time access to data.
- OLTP services help to provide better security by applying multiple security features.
- OLTP services help in making better decision making by providing accurate data or current data.
- OLTP Services provide Data Integrity, Consistency, and High Availability to the data.

Drawbacks of OLTP Services
- OLTP has limited analysis capability as they are not capable of intending complex analysis or reporting.
- OLTP has high maintenance costs because of frequent maintenance, backups, and recovery.
- OLTP Services get hampered in the case whenever there is a hardware failure which leads to the failure of online transactions.
- OLTP Services many times experience issues such as duplicate or inconsistent data.

## Difference between OLAP and OLTP

| Category            | OLAP                                                                               | OLTP                                                                                       |
| ------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Definition          | It is well-known as an online database query management system.                    | It is well-known as an online database modifying system.                                   |
| Data source         | Consists of historical data from various Databases.                                | Consists of only operational current data.                                                 |
| Method used         | It makes use of a data warehouse.                                                  | It makes use of a standard database management system (DBMS).                              |
| Application         | It is subject-oriented. Used for Data Mining, Analytics, Decisions making, etc.    | It is application-oriented. Used for business tasks.                                       |
| Normalized          | tables are not normalized.                                                         | tables are normalized (3NF).                                                               |
| Usage of data       | The data is used in planning problem-solving, and decision- making.                | The data is used to perform day-to-day fundamental operations.                             |
| Task                | It provides a multi-dimensional view of different business tasks.                  | It reveals a snapshot of present business tasks.                                           |
| Purpose             | It serves the purpose to extract information for analysis and decision-making.     | It serves the purpose to Insert, Update, and Delete information from the database.         |
| Volume of data      | A large amount of data is stored typically in TB, PB                               | The size of the data is relatively small as the historical data is archived in MB, and GB. |
| Queries             | Relatively slow as the amount of data involved is large. Queries may take hours.   | Very Fast as the queries operate on 5% of the data.                                        |
| Update              | The OLAP database is not often updated. As a result, data integrity is unaffected. | The data integrity constraint must be maintained in an OLTP database.                      |
| Backup and Recovery | It only needs backup from time to time as compared to OLTP.                        | The backup and recovery process is maintained rigorously                                   |
| Processing time     | The processing of complex queries can take a lengthy time.                         | It is comparatively fast in processing because of simple and straightforward queries.      |
| Types of users      | This data is generally managed by CEO, MD, and GM.                                 | This data is managed by clerksForex and managers.                                          |
| Operations          | Only read and rarely write operations.                                             | Both read and write operations.                                                            |
| Updates             | With lengthy, scheduled batch operations, data is refreshed on a regular basis.    | The user initiates data updates, which are brief and quick                                 |
| Nature of audience  | The process is focused on the customer.                                            | The process is focused on the market.                                                      |
| Database Design     | Design with a focus on the subject.                                                | Design that is focused on the application.                                                 |
| Productivity        | Improves the efficiency of business analysts.                                      | Enhances the user’s productivity.                                                          |
