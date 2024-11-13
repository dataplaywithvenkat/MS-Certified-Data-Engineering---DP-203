# Determine operational needs

## Table of Contents
1. [Introduction](#introduction)
2. [Identifying Data Types](#identifying-data-types)
3. [Questions to Ask When Determining Data Usage](#questions-to-ask-when-determining-data-usage)
4. [Examples of Online Retailer Datasets](#examples-of-online-retailer-datasets)
    1. [Product Catalog Data](#product-catalog-data)
    2. [Photos and Videos](#photos-and-videos)
    3. [Business Data](#business-data)
5. [Conclusion](#conclusion)

---

## Introduction

Once you've identified the kind of data you're dealing with—structured, semi-structured, or unstructured—the next step is to determine how you'll use the data. For example, as an online retailer, you know customers need quick access to product data, while business users need to run complex analytical queries. As you work through these requirements, taking your data classification into account, you can start to plan your data storage solution.

## Identifying Data Types

The first step is to classify your data into one of the following categories:
- **Structured Data**: Data that is highly organized and stored in tables, such as relational databases.
- **Semi-Structured Data**: Data that has some structure but does not conform to strict schema, such as JSON or XML.
- **Unstructured Data**: Data with no specific structure, like text files, images, or videos.

After identifying your data type, consider how each data type will be used to determine the best storage solution.

## Questions to Ask When Determining Data Usage

When planning your data storage, here are some important questions to consider:

- What are the main operations you'll be completing on each data type?
- What are the performance requirements?
    - Will you be doing simple lookups using an ID?
    - Do you need to query the database from one or more fields?
    - How many create, update, and delete operations do you expect?
    - Do you need to run complex analytical queries?
    - How quickly do these operations need to complete?

These questions will help you determine the optimal storage solution for your data.

## Examples of Online Retailer Datasets

### Product Catalog Data

For product catalog data, customer needs are the highest priority. Customers will want to:
- Query the product catalog to find specific products, such as "all men's shoes," then narrow that down to "men's shoes on sale" and finally "men's shoes on sale in a particular size."

This requires:
- A large number of **read operations**, especially for querying specific attributes like product categories, sizes, and sales status.
- **Write operations** for updating product quantities when orders are placed. These updates need to be fast so that users don’t end up with items in their shopping carts that have just sold out.

It's important to determine the priorities for all database users, not just the primary ones, to ensure efficient data storage and retrieval.

### Photos and Videos

Photos and videos displayed on product pages have different requirements:
- **Fast retrieval times**: Photos and videos need to be displayed quickly alongside product data.
- These files don’t need to be queried independently; instead, they can be linked via the product data (e.g., through a product ID or URL).
- **Minimal updates**: While users can upload new photos (e.g., product reviews), updates to existing photos or videos are less frequent. Employees may upload or delete product photos from vendors, but this doesn't need to happen as quickly as product data updates.

### Business Data

Business data is typically read-only:
- **Analysis on historical data**: Business data is primarily used for analysis and is not updated based on the analysis.
- **No real-time updates needed**: Users don't expect complex analytics to run instantly, so latency in results is acceptable.
- **Multiple datasets**: Business data is stored across different datasets with different access rights. Business analysts can read from all datasets, but they may have limited write access.

## Conclusion

When deciding on what storage solution to use, it’s crucial to consider how your data will be used:
- **Frequency of access**: How often is the data accessed and updated?
- **Read-only data**: Is your data read-only, or does it require frequent updates?
- **Query performance**: Does query time matter for your data operations?

Answering these questions will guide you in choosing the best storage solution for your data.
