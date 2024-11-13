# Decide how many storage accounts you need

## Table of Contents
1. [Introduction](#introduction)
2. [Azure Storage Services Overview](#azure-storage-services-overview)
3. [What is a Storage Account?](#what-is-a-storage-account)
4. [Azure Storage Account Settings](#azure-storage-account-settings)
    - [Subscription](#subscription)
    - [Location](#location)
    - [Performance](#performance)
    - [Replication](#replication)
    - [Access Tier](#access-tier)
    - [Secure Transfer](#secure-transfer)
    - [Virtual Networks](#virtual-networks)
5. [Managing Multiple Storage Accounts](#managing-multiple-storage-accounts)
    - [Data Diversity and Separation](#data-diversity-and-separation)
    - [Cost Optimization](#cost-optimization)
    - [Administrative Considerations](#administrative-considerations)
6. [Conclusion](#conclusion)

---

## Introduction
Organizations often have multiple storage accounts to meet various requirements. For example, a chocolate manufacturer might have separate storage accounts for private business data and consumer-facing files. Understanding the policy factors controlled by a storage account can help you decide how many accounts you need. Azure offers various ways to store data, including databases, messaging services, and file storage options.

## Azure Storage Services Overview
Microsoft Azure provides multiple data storage solutions, such as:

- **Databases**: Azure SQL Database, Azure Cosmos DB, Azure Table Storage.
- **Messaging Services**: Azure Queues, Azure Event Hubs.
- **File Storage**: Azure Files, Azure Blobs.

Azure Storage includes four primary services:
- **Azure Blobs**
- **Azure Files**
- **Azure Tables**
- **Azure Queues**

These services are often grouped together in a single storage account because they are fundamental cloud-based storage solutions that are frequently used together in applications.

## What is a Storage Account?
A storage account in Azure is a container for grouping a set of Azure Storage services. This account lets you manage these services as a collective unit. Only services under the Azure Storage umbrella can be included within a storage account.

- Each storage account is a resource stored within a **resource group**.
- An Azure **subscription** can contain multiple resource groups, each with its own storage accounts.
- Services like **Azure Cosmos DB** and **Azure SQL Database** are managed independently and cannot be included in a storage account.

### Example
A typical storage account might include:
- **Blobs** for unstructured data
- **Files** for file shares
- **Queues** for messaging
- **Tables** for structured, NoSQL data

Combining these services into a single storage account allows for centralized management. Settings specified during account creation or modifications apply to all services within that account.

## Azure Storage Account Settings
A storage account's settings determine how its contained services are managed. Key settings include:

### Subscription
- Defines which Azure subscription is billed for the services in the account.

### Location
- Specifies the **data center** where the services are hosted. Choosing the right location can optimize performance.

### Performance
Azure offers two performance tiers:
- **Standard**: Supports all data services (Blobs, Files, Queues, Tables) using **magnetic disk drives**.
- **Premium**: Optimized for block blobs, append blobs, and high-performance file storage using **solid-state drives (SSD)**.

### Replication
Ensures data durability by automatically creating copies of your data:

- **Locally Redundant Storage (LRS)**: Maintains three copies of your data within a single data center.
- **Geo-Redundant Storage (GRS)**: Replicates data across multiple data centers, providing additional protection against regional failures.

### Access Tier
Applicable only to Azure Blobs, this setting optimizes storage costs based on access frequency:
- **Hot**: Low latency but higher cost.
- **Cool**: Lower cost but higher access latency.

### Secure Transfer
- Controls protocol security by requiring **HTTPS** connections for accessing data. Enabling this setting enhances security.

### Virtual Networks
- Restricts inbound access to specific virtual networks, adding an extra layer of security.

## Managing Multiple Storage Accounts
The need for multiple storage accounts arises from different data requirements:

### Data Diversity and Separation
- **Geographical Compliance**: Data specific to a region may need to be stored within that region's data center.
- **Public vs. Private Data**: Proprietary data may require additional security settings, such as virtual networks, whereas public data might not.

### Cost Optimization
Azure storage accounts themselves are cost-free, but their settings affect service costs. For example:
- Use **GRS** for critical data that needs high availability.
- Use **LRS** for non-critical data to reduce costs.

### Administrative Considerations
- Each storage account requires management. More accounts mean higher complexity but allow finer control over data partitioning.
- You might create separate accounts to manage billing for different departments or projects.

### Examples
- **Scenario 1**: A company with operations in multiple countries may need a separate storage account for each region to comply with data residency laws.
- **Scenario 2**: An organization could separate storage accounts for sensitive financial data versus public marketing content.

## Conclusion
Azure Storage Accounts offer a versatile way to manage diverse data requirements with settings that affect performance, security, and cost. By analyzing your data needs, you can partition data into storage accounts based on characteristics like location, access requirements, and replication strategies. This approach helps balance performance, security, and cost-efficiency.

Here's a detailed comparison table of **Locally Redundant Storage (LRS)** and **Geo-Redundant Storage (GRS)** in Azure:

| **Feature**                           | **Locally Redundant Storage (LRS)**                                                                            | **Geo-Redundant Storage (GRS)**                                                                                   |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| **Definition**                        | Stores data synchronously across **three copies** within a **single data center** in a single Azure region.    | Stores data synchronously across **three copies** within a primary region (like LRS) and asynchronously replicates data to another **secondary region** hundreds of miles away. |
| **Use Case**                          | - Ideal for cost-sensitive applications requiring basic protection against hardware failures.<br>- Suitable for non-critical data where data loss in the event of a regional failure is acceptable. | - Best for applications needing higher durability and disaster recovery protection.<br>- Suitable for critical workloads requiring cross-region redundancy to ensure data availability in case of regional outages. |
| **Data Replication Scope**            | - Replication occurs **within a single data center** in the primary region.                                    | - Replication occurs **across two geographically separated regions** (primary and secondary).<br>- Asynchronous replication ensures copies are made to a second region after they're committed to the primary region. |
| **Durability**                        | - Offers **99.999999999% (11 nines)** durability for objects over a given year.                                | - Provides higher durability with **99.99999999999999% (16 nines)** durability over a given year due to cross-region replication. |
| **Availability SLA**                  | - **99.9% availability SLA** for read and write operations.                                                    | - **99.9% availability SLA** for read and write operations on the primary region.<br>- Provides a **read-access GRS (RA-GRS)** option with **99.99% availability SLA** for read operations from the secondary region. |
| **Read Access from Secondary Region** | - **Not available**; only the primary region is accessible.                                                   | - **Available with RA-GRS** (Read-Access Geo-Redundant Storage), which allows read access to data from the secondary region if the primary region is unavailable. |
| **Disaster Recovery**                 | - Provides protection against hardware failures within the same data center.<br>- **No protection** against region-wide outages (e.g., natural disasters). | - Offers protection against regional disasters by replicating data to a distant secondary region.<br>- Ensures data availability even if the primary region is entirely unavailable. |
| **Data Consistency**                  | - Ensures **strong consistency** within the same data center since all copies are within a single region.     | - Provides **eventual consistency** for data in the secondary region due to asynchronous replication.<br>- Data in the secondary region may lag behind the primary region data. |
| **Cost**                              | - **Lower cost** compared to GRS due to single-region storage.                                                | - **Higher cost** than LRS because of the additional cross-region replication and storage in the secondary region. |
| **Ideal Scenarios**                   | - Suitable for development and test environments.<br>- Backup of non-critical data.<br>- Workloads where regional redundancy is not a concern. | - Suitable for critical applications requiring disaster recovery and high availability across regions.<br>- Financial, healthcare, and government applications needing compliance and data protection. |
| **Examples of Use**                   | - Hosting temporary data like caches or logs.<br>- Internal reports or analytics where data loss is tolerable. | - Backing up databases where recovery is crucial.<br>- Hosting applications with a global user base needing low-latency reads in multiple regions. |
| **Azure Storage Tiers Compatibility** | - Supported across **Hot, Cool, and Archive** tiers.                                                          | - Supported across **Hot and Cool** tiers, with **Archive tier** available in primary region only; not applicable to secondary. |

### Key Takeaways:
- **LRS** is best for scenarios where cost is a priority and regional redundancy is not required.
- **GRS** is ideal for applications where data durability, regional disaster recovery, and cross-region data availability are critical.

When choosing between LRS and GRS, consider factors such as data criticality, compliance requirements, budget, and the need for disaster recovery.

Here's a detailed comparison table for the following Azure storage and database solutions: **Azure SQL Database**, **Azure Cosmos DB**, **Azure Table Storage**, **Azure Queues**, **Azure Event Hub**, **Azure Files**, and **Azure Blob Storage**.

| **Feature**                            | **Azure SQL Database**                                                                                                                                                    | **Azure Cosmos DB**                                                                                                                     | **Azure Table Storage**                                                                                                                 | **Azure Queues**                                                                                                                        | **Azure Event Hub**                                                                                                                    | **Azure Files**                                                                                                                        | **Azure Blob Storage**                                                                                                                 |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| **Purpose**                            | Fully managed **relational database** service for **structured data** with rich query capabilities using **T-SQL**.                                                       | Globally distributed, **multi-model NoSQL database** service for **semi-structured and unstructured data**.                              | Simple, scalable **NoSQL key-value store** for semi-structured data.                                                                    | **Message queueing** for decoupling application components and ensuring asynchronous processing.                                        | Real-time **data ingestion and event streaming** for big data pipelines, analytics, and telemetry.                                      | **Fully managed file shares** in the cloud that can be accessed via SMB protocol.                                                      | **Object storage** solution for storing unstructured data like files, images, and backups.                                             |
| **Data Structure**                     | **Structured** data with fixed schemas (tables, columns, rows).                                                                     | **Schema-agnostic**; supports key-value, document, column-family, and graph models.                                                    | **Key-value pairs** with a simple structure (partition key, row key, properties).                                                      | **FIFO (First-In-First-Out)** message storage with optional time-to-live (TTL) for messages.                                           | Streams of **events** with high-throughput, low-latency, and ordered delivery.                                                         | **Hierarchical file system** with directories and files.                                                                               | **Blob (Binary Large Object)** storage for large files, optimized for streaming and large-scale data.                                   |
| **Query Language**                     | Supports **T-SQL** for complex queries, stored procedures, and transactions.                                                      | Supports **SQL (Core API)**, **MongoDB API**, **Cassandra API**, **Gremlin API**, and **Table API** for various NoSQL models.           | **OData** queries with limited filtering and projection capabilities.                                                                  | No query language; operations include enqueue, dequeue, and peek messages.                                                             | Uses **Event Hub Capture**, **Stream Analytics**, or consumer groups for data processing.                                              | No query language; uses standard file system operations (e.g., list, read, write).                                                    | No query language; uses **Azure Blob SDK** or REST API for operations (e.g., put, get, delete).                                        |
| **Scalability**                        | - **Scale up**: Increase DTUs or vCores.<br>- **Scale out**: Use read replicas and sharding.                                      | - **Horizontal scaling** with automatic partitioning and global distribution.<br>- Supports **unlimited throughput and storage**.       | - **Horizontal scaling** by partitioning based on partition keys.<br>- Suitable for large datasets.                                    | - Scales based on the number of messages and queue size.<br>- Supports **unlimited message size** with max size 64 KB/message.         | - Highly scalable with **throughput units** (TU) for managing event ingestion.<br>- Supports millions of events per second.            | - Scales up to **100 TiB** per share.<br>- Supports **concurrent access** from multiple VMs.                                          | - Supports **Hot, Cool, and Archive tiers** for scalability.<br>- Can scale to **exabytes** of data.                                   |
| **Consistency**                        | Strong consistency with **ACID transactions**.                                                                                     | Offers **5 consistency models**: Strong, Bounded Staleness, Session, Consistent Prefix, and Eventual.                                  | **Strong consistency** within a single entity group transaction.                                                                      | **At-least-once delivery**; no strict ordering guarantees.                                                                            | **Eventual consistency** with ordered partitioning and at-least-once delivery.                                                        | Strong consistency for file operations.                                                                                                | **Eventual consistency** by default, but can achieve strong consistency with append blobs.                                            |
| **Use Cases**                          | - OLTP applications.<br>- Enterprise applications requiring complex queries and reporting.<br>- Business apps with transactional workloads. | - IoT, real-time analytics, and mobile apps needing low-latency, globally distributed data.<br>- Multi-model data storage.             | - Storing user profiles, session data, and configuration settings.<br>- Applications needing simple, structured storage.               | - Decoupling microservices.<br>- Asynchronous processing for tasks like order processing, background jobs.                             | - Real-time analytics, fraud detection, IoT telemetry, and live dashboards.<br>- High-throughput data ingestion scenarios.             | - Lift-and-shift migration of on-premises file shares.<br>- Shared storage for legacy applications.<br>- Persistent storage for VMs.   | - Backup and disaster recovery.<br>- Media streaming, archiving, and static content hosting.<br>- Storing large datasets for analytics. |
| **Data Replication**                   | - **Geo-replication** (Active Geo-Replication) for high availability.                                                             | - **Multi-region replication** with automatic failover and read/write endpoints.<br>- **Multi-master replication** support.            | - **LRS, GRS, RA-GRS** replication options.                                                                                           | - **LRS, GRS, RA-GRS** replication options for redundancy.                                                                            | - **LRS** or **Zone-redundant storage (ZRS)** for resiliency.                                                                         | - **LRS, ZRS, GRS, RA-GRS** replication options.                                                                                      | - **LRS, ZRS, GRS, RA-GRS** options for durability.                                                                                   |
| **Security**                           | - **Built-in threat detection**, TDE, Always Encrypted.<br>- VNet integration, Private Link.                                      | - **End-to-end encryption** (at-rest and in-transit).<br>- VNet integration, Private Link, and Role-Based Access Control (RBAC).       | - Supports **Shared Access Signatures (SAS)** and Azure AD authentication.                                                            | - Supports **Shared Access Signatures (SAS)** for secure message access.                                                              | - Supports **Azure AD authentication** and role-based access.<br>- Network Security Groups (NSG) and Private Link.                    | - **Azure AD authentication**, SMB encryption, and VNet integration.                                                                  | - **Encryption at rest**, SAS tokens, and Azure AD authentication.<br>- Supports firewall rules and VNet integration.                 |
| **Data Retention**                     | - Supports **point-in-time restore** and **long-term backup** retention policies.                                                | - Configurable **TTL (Time-to-Live)** for documents and collections.                                                                   | - No native retention policy; handled at the application level.                                                                      | - Supports configurable **TTL** for messages.                                                                                         | - Data retention based on **Event Hub Capture** settings.                                                                             | - Supports configurable **retention policies** for file versions.                                                                     | - Configurable **lifecycle management policies** for automatic data archiving.                                                        |
| **Cost Model**                         | - Billed based on **DTUs/vCores, storage, and backup**.                                                                           | - Billed based on **provisioned throughput (RU/s), storage, and regions used**.                                                        | - **Pay-as-you-go** pricing for transactions and storage.                                                                             | - **Pay-as-you-go** based on the number of operations and storage used.                                                               | - **Throughput units (TUs)** or **Capacity units** for dedicated environments.<br>- Ingestion and retention charges apply.            | - **Pay-as-you-go** based on provisioned storage and operations.<br>- Additional charges for snapshots and backups.                   | - Billed based on **storage tier, operations, and data egress**.                                                                      |

### Key Takeaways:
- **Azure SQL Database**: Best for structured, transactional workloads with complex queries.
- **Azure Cosmos DB**: Ideal for globally distributed, low-latency NoSQL data across multiple models.
- **Azure Table Storage**: Suitable for simple, key-value NoSQL storage with low-cost options.
- **Azure Queues**: Great for message decoupling in distributed systems and background processing.
- **Azure Event Hub**: Designed for high-throughput event streaming and real-time analytics.
- **Azure Files**: Ideal for SMB file sharing and lift-and-shift migrations.
- **Azure Blob Storage**: Best for storing large objects like media files, backups, and unstructured data.

