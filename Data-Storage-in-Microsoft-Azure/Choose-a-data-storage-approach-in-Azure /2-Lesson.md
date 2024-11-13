# Classify your data

## Table of Contents
- [Introduction](#introduction)
- [Types of Data](#types-of-data)
  - [Structured Data](#structured-data)
  - [Semi-Structured Data](#semi-structured-data)
  - [Unstructured Data](#unstructured-data)
- [Data Classification for Online Retail Business](#data-classification-for-online-retail-business)
  - [Product Catalog Data](#product-catalog-data)
  - [Photos and Videos](#photos-and-videos)
  - [Business Data](#business-data)
- [Summary](#summary)

## Introduction
An online retail business generates different types of data, each of which may require a different storage solution. The three main types of data include **structured**, **semi-structured**, and **unstructured**. Understanding the differences between these data types can help businesses choose the appropriate storage systems and manage their data more effectively.

## Types of Data

### Structured Data
Structured data, often referred to as **relational data**, follows a **strict schema**. All data points have the same properties, and this consistency allows for easy querying using **SQL (Structured Query Language)**. Structured data is ideal for applications such as **Customer Relationship Management (CRM)**, **reservation systems**, and **inventory management systems**.

- **Storage**: Structured data is stored in **database tables**, typically in rows and columns, with **key columns** linking data across tables. This organization allows for easy searching and data retrieval.
- **Example**: A student table linked to a course table, with relationships defined by grades.
- **Limitations**: The main challenge with structured data is the difficulty in evolving the schema. For instance, adding a new column to the table requires updating all existing rows to ensure consistency.

### Semi-Structured Data
Semi-structured data is **less organized** than structured data, and it doesn't fit neatly into tables. However, it still contains **tags** that help define its structure, often in the form of **key-value pairs**. This data type is also referred to as **non-relational** or **NoSQL** data.

- **Data Formats**: Semi-structured data is often expressed in **serialization languages** such as **JSON** (JavaScript Object Notation), **XML** (Extensible Markup Language), and **YAML** (YAML Ain't Markup Language). These formats allow data to be exchanged between different systems with varying infrastructure, such as mobile devices and web applications.
  - **XML**: Initially popular, XML is widely supported across platforms and is both **human-readable** and **machine-readable**. It allows the expression of relationships between data using tags.
  - **JSON**: A **lightweight** data format that is less verbose than XML and often used for **web services**. Its simplicity makes it popular for web development.
  - **YAML**: A human-friendly format that is often used for configuration files. Its simplicity and readability make it attractive, though it doesn't yet have the support that XML and JSON have in programming languages.
- **Example**: A person’s hobbies represented in XML, JSON, or YAML formats.
- **Flexibility**: Unlike structured data, semi-structured data allows new attributes to be added without affecting existing data, making it more adaptable for evolving business needs.

### Unstructured Data
Unstructured data lacks a clear schema or organization, making it difficult to fit into traditional tables or relational formats. This type of data often comes in the form of **media files** (photos, videos, audio files) or documents.

- **Examples**: **Media files** such as photos, videos, and audio files, and **office files** like Word documents, text files, and **log files**.
- **Storage**: Unstructured data is typically stored as **files** and may include **metadata** but lacks a formalized structure for the content itself.

## Data Classification for Online Retail Business

### Product Catalog Data
Product catalog data for an online retail business is mostly **structured** at first. Each product has consistent attributes such as **product SKU**, **description**, **quantity**, **price**, **size options**, **color options**, **photos**, and **videos**. However, as the business grows and new products are added, the catalog may need to evolve, which could cause it to transition to **semi-structured data**.

- **Example**: If new products, such as **Bluetooth-enabled shoes**, are introduced, they may require new attributes that aren't shared by all products. For example, the addition of a **Bluetooth-enabled** field for new shoes might require flexibility in the catalog to allow some products to have unique properties.
- If the introduction of new attributes, such as **Bluetooth**, is expected to become more common, the data might move toward being **semi-structured**, with each product having unique fields but still retaining some consistency in the schema.

### Photos and Videos
The media files associated with products, such as **photos** and **videos**, are classified as **unstructured data**. Although these files may contain **metadata** (e.g., file size, resolution), the actual content (image or video) does not fit into a traditional structured format.

- **Example**: Product images and videos displayed on e-commerce sites are **unstructured data**.

### Business Data
Business data used for **inventory management** and **sales tracking** must be **structured** to allow **aggregation** and **comparison** over time. For example, to evaluate inventory pipelines and review sales data over multiple months, the data must be organized so that one month's data can be compared with another's.

- **Example**: Monthly sales data or inventory data that needs to be aggregated and queried in a structured manner to perform business intelligence tasks.

## Summary
In this lesson, you learned how data in an online retail business can be classified into three categories:

- **Structured Data**: Data that is highly organized, often in the form of relational databases with rows and columns.
- **Semi-Structured Data**: Data that is organized with tags or key-value pairs, such as XML, JSON, or YAML, but does not fit neatly into relational tables.
- **Unstructured Data**: Data that does not have a schema or organization, including media files and documents.

Each type of data has different storage and management requirements. Understanding the differences between these types will help you choose the appropriate solution for storing, processing, and analyzing your business data.
