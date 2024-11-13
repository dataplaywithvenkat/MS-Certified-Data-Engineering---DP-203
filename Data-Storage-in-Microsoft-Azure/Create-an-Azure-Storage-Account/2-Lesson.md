# Azure Storage Accounts: Advanced Settings Overview

## Table of Contents
- [Introduction](#introduction)
- [Key Storage Account Settings](#key-storage-account-settings)
  - [1. Name](#1-name)
  - [2. Deployment Model](#2-deployment-model)
    - [Resource Manager](#resource-manager)
    - [Classic](#classic)
  - [3. Account Kind](#3-account-kind)
    - [Storage v2 (General Purpose v2)](#storage-v2-general-purpose-v2)
    - [Storage (General Purpose v1)](#storage-general-purpose-v1)
    - [Blob Storage](#blob-storage)
- [Recommendations for New Storage Accounts](#recommendations-for-new-storage-accounts)
- [Conclusion](#conclusion)

---

## Introduction
In Azure, a storage account is a resource that provides access to Azure storage services. While there are many settings that impact the data stored within an account, there are also settings that apply specifically to the account itself. These include **Name**, **Deployment Model**, and **Account Kind**. Understanding these settings is crucial for effective management and cost optimization.

---

## Key Storage Account Settings

### 1. Name
- Every storage account must have a unique **Name**.
- The name must adhere to the following rules:
  - Must be **globally unique** across all of Azure.
  - Only **lowercase letters** and **digits** are allowed.
  - Length must be between **3 to 24 characters**.

### 2. Deployment Model
The **Deployment Model** determines how Azure organizes your resources and how you interact with them via APIs. There are two deployment models in Azure:

#### Resource Manager
- The **Resource Manager** is the **current model** and uses the Azure Resource Manager API.
- This model is recommended for all new resources as it offers better management capabilities.
- Resources under this model are grouped into **Resource Groups**, allowing you to manage multiple resources as a single unit.
- Most Azure services, including storage accounts, virtual machines, and virtual networks, use this model.

#### Classic
- The **Classic** model uses the older Azure Service Management API.
- It is primarily a legacy option and is not recommended for new deployments.
- Resources deployed using the Classic model **cannot** be managed using modern features available in the Resource Manager.

> **Tip:** Microsoft advises using the **Resource Manager** for all new resources to take advantage of the latest features and management capabilities.

### 3. Account Kind
**Account Kind** determines the available data services and the pricing model for the storage account. There are three types:

#### Storage v2 (General Purpose v2)
- This is the **current standard offering**.
- Supports **all storage types** (e.g., blobs, files, queues, tables) and **latest features**.
- Recommended for most scenarios as it offers the best performance and flexibility.

#### Storage (General Purpose v1)
- Supports all storage types, similar to Storage v2.
- May not support all of the latest features.
- Typically used for legacy applications.
- Offers slightly **lower transaction costs**, which can be beneficial for workloads with high transaction volumes but minimal feature requirements.

#### Blob Storage
- Dedicated for storing **block blobs** and **append blobs** only.
- It is a **legacy option** and is typically used for applications that only require object storage.
- Not recommended for new deployments unless there is a specific requirement.

> **Recommendation:** For new storage accounts, use **Storage v2 (General Purpose v2)** unless you have a specific need that aligns with the benefits of General Purpose v1 or Blob Storage.

---

## Recommendations for New Storage Accounts
- **Use Resource Manager**: It is the modern deployment model that supports all the latest features, provides better management, and aligns with Azure's best practices.
- **Choose Storage v2 (General Purpose v2)**: This is the recommended account kind due to its support for all storage services and latest features.
- Consider **General Purpose v1** only if your workload has unique transaction cost requirements that align with its pricing structure.
- Avoid using **Classic deployment model** and **Blob Storage** kind unless you are maintaining legacy applications.

---

## Conclusion
Azure storage account settings like **Name**, **Deployment Model**, and **Account Kind** are foundational to managing storage resources effectively. For most use cases, choosing the **Resource Manager** deployment model and **Storage v2 (General Purpose v2)** account kind provides the best combination of features, performance, and cost-effectiveness.

By making informed decisions about these settings, you can optimize storage management and ensure that your resources align with your organizational requirements.

---

