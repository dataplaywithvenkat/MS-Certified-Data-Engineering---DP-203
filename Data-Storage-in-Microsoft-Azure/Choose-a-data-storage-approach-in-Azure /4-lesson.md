# What is NO-SQL/Semi Structured Data

# NoSQL Overview

## Table of Contents
1. [Introduction](#introduction)
2. [Problems with Relational Databases](#problems-with-relational-databases)
3. [What is NoSQL?](#what-is-nosql)
4. [NoSQL Data Models](#nosql-data-models)
    1. [Key-Value Databases](#key-value-databases)
    2. [Graph Databases](#graph-databases)
    3. [Document Databases](#document-databases)
5. [Why NoSQL?](#why-nosql)
6. [NoSQL and Cloud Providers](#nosql-and-cloud-providers)

---

## Introduction

In this video, we're going to talk about NoSQL, giving you an overview of what it is and how it can help you.

## Problems with Relational Databases

When it comes to storing data, there are a few options you can choose from. For a long time, the go-to data storage technique was relational databases. However, over time it became clear that relational databases suffer from a few problems. For instance:

- Retrieving an object with all relevant data can lead to complex queries.
- SQL queries aren't suited well for object-oriented data structures.
- This results in poor performance when querying large amounts of data.

Hence, the creation of NoSQL.

## What is NoSQL?

NoSQL takes a bit of a different approach when thinking about databases. For one, it is not a relational database nor does it rely on tables or SQL. Instead, it offers a set of different data models for managing the needs of your data in a flexible way.

NoSQL has gained a lot of popularity due to its ease of use and scalability.

## NoSQL Data Models

Let's discuss three examples of NoSQL data models: **key-value**, **graph**, and **document**. Each model has different use cases and excels in different areas.

### Key-Value Databases

Key-value databases store data in key-value pairs, which makes querying faster. With key-value databases, you don't use a query language, but instead, you use simple commands like:

- `get`
- `put`
- `delete`

These commands allow for fast data retrieval.

### Graph Databases

Graph databases use nodes that contain records that point to other nodes. This structure ultimately creates links of relationships, which helps speed up query times. Graph databases are particularly useful for scenarios where relationships between data elements are important, such as social networks.

### Document Databases

Document databases store data using a markup language like **JSON** or **XML**. Because of this flexibility, you can store any data in any structure you want, making document databases highly adaptable to various needs.

## Why NoSQL?

Although relational databases have been around for a long time, they are starting to fall short when dealing with modern problems. As a result, NoSQL is becoming more and more popular due to its ability to handle large amounts of data efficiently and its ease of use.

## NoSQL and Cloud Providers

Large cloud providers, like **Azure**, are offering NoSQL database solutions, such as **Azure Cosmos DB**, to allow everyone to get the benefits. This makes the transition to NoSQL even easier, especially if you're new to the concept.
