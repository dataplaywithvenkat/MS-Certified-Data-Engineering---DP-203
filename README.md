# MS Certified Data Engineering DP-203

# Important Notes

## Detailed comparison of **XML**, **JSON**, and **YAML**:

| **Feature**              | **XML (Extensible Markup Language)**                                  | **JSON (JavaScript Object Notation)**                               | **YAML (YAML Ain't Markup Language)**                               |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------|---------------------------------------------------------------------|
| **Readability**           | Verbose and complex, harder for humans to read and write.            | Lightweight and human-readable, easier to understand at a glance.  | Very human-friendly, uses indentation for easy reading and writing. |
| **Data Structure**        | Uses tags surrounded by angle brackets `<tag></tag>` to structure data. | Uses curly braces `{}` and square brackets `[]` for objects and arrays. | Uses indentation to denote structure, no brackets or quotes.       |
| **Syntax Complexity**     | Complex syntax, includes opening/closing tags and attributes.        | Simple syntax, with fewer symbols and simpler structure.           | Simplified syntax with minimal punctuation, indentation-based.     |
| **File Size**             | Generally larger due to verbose tags and extra metadata.             | Generally smaller, more compact than XML.                           | Often more compact than both XML and JSON due to fewer characters. |
| **Data Types**            | Limited built-in support for data types (mostly string-based).       | Supports primitive data types like strings, numbers, booleans, and arrays. | Supports data types but relies on implicit typing and flexible structure. |
| **Schema Support**        | Strong schema support (XML Schema).                                  | No native schema support, but external validation can be used.     | No built-in schema support, flexible and free-form.                |
| **Comments**              | Supports comments using `<!-- comment -->`.                          | Does not support comments natively.                                | Supports comments using `# comment`.                               |
| **Namespaces**            | Supports namespaces to avoid conflicts in tag names.                 | No native namespace support.                                       | No support for namespaces.                                          |
| **Whitespace Sensitivity**| Whitespace is significant; spaces, tabs, and newlines are considered. | Whitespace is not significant, except for inside strings.          | Whitespace is very significant; indentation defines the structure.  |
| **Validation**            | Supports validation through **XML Schema Definition (XSD)**.        | No native validation; validation can be done with external tools.  | No formal validation mechanisms; uses external tools for validation.|
| **Parsing Speed**         | Slower parsing due to its verbosity and complexity.                  | Faster parsing as it has a simpler structure compared to XML.      | Fast parsing, lightweight due to minimal syntax.                   |
| **Popularity**            | Historically popular, still used in legacy systems, document formats. | Extremely popular for web development and APIs, particularly in REST. | Growing in popularity for configuration files, CI/CD pipelines, etc. |
| **Error Handling**        | Difficult to handle errors, and small mistakes can cause failure.    | Easier to handle errors, simpler format.                          | Easier to handle errors, but improper indentation can cause issues. |
| **Use Case**              | Ideal for document formats, complex data structures, and legacy systems. | Common in web APIs, JavaScript applications, data exchange.       | Best for configuration files, logs, and when human readability is a priority. |
| **Serialization/Deserialization** | Slow serialization and deserialization due to verbose format.    | Fast serialization and deserialization due to simpler format.     | Very fast serialization and deserialization, human-readable format. |
| **Tool Support**          | Widely supported across many platforms and languages.                | Supported in nearly all modern programming languages.              | Supported in most languages, but less widespread than XML and JSON.  |

---

## Comparison of Azure Storage Services

| **Service**               | **Best For**                  | **Data Type**        | **Max Size**         | **Access Protocol**  | **Query Capabilities** |
|---------------------------|-------------------------------|----------------------|----------------------|----------------------|------------------------|
| Azure Blob Storage        | Backups, Unstructured Data    | Binary, Text         | 4.75 TB per blob     | REST API             | No                     |
| Azure Files               | File Sharing, Lift-and-Shift  | File Data            | 5 TiB per share      | SMB, NFS             | No                     |
| Azure Queue               | Decoupling Apps, Async Jobs   | Messages             | 64 KB per message    | REST API             | No                     |
| Azure Table Storage       | NoSQL Storage, Structured Data| Key-Value            | 1 MB per entity      | REST API             | Limited (No Joins)     |

---

## Comparison: Structured vs Unstructured Data

| **Feature**              | **Structured Data**                               | **Unstructured Data**                           |
|--------------------------|---------------------------------------------------|-------------------------------------------------|
| **Schema**               | Predefined at design time                         | Defined at read time                            |
| **Storage System**       | Relational databases (e.g., Azure SQL Database)   | NoSQL databases (e.g., Azure Cosmos DB)         |
| **Data Types**           | Tabular data (e.g., integers, strings)            | Binary, images, audio, semi-structured (JSON)   |
| **Query Language**       | SQL (e.g., T-SQL)                                 | Varies (e.g., NoSQL APIs, LINQ)                 |
| **Flexibility**          | Low; schema changes are costly                    | High; can adapt to new data types easily        |
| **Use Cases**            | Financial transactions, customer databases        | Social media data, IoT sensor data              |

---
