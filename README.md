<p align="center">
  <h1 align="center">Neo4j Graph Database</h1>
  <p align="center">
    <strong>English</strong> | <a href="README_ZH.md">简体中文</a>
  </p>

## Table of Contents

- [Repository Introduction](#project-introduction)
- [Prerequisites](#prerequisites)
- [Image Description](#image-description)
- [Get Help](#get-help)
- [How to Contribute](#how-to-contribute)

## Project Introduction

[[openmemory-mcp](https://github.com/mem0ai/mem0/tree/main/openmemory) OpenMemory is your LLM personal memory layer, private, portable, and open-source. Your memory is stored locally, giving you complete control over your data. Build AI applications using personalized memory while ensuring data security

### **Core Features:**

- **Cross session memory storage**:Support long-term storage and calling of any text block, enabling AI to "remember" previous content in each interaction without having to start from scratch
- **Intelligent retrieval mechanism**:Utilizing Qdrant vector database to achieve efficient retrieval based on semantic relevance, surpassing the limitations of traditional keyword matching
- **Fully local deployment **:The entire system is built on Docker, PostgreSQL, and Qdrant, and all data is processed and stored locally without sending any information externally, ensuring privacy and security
- **Cross tool memory sharing** : Clients that support MCP protocol (such as Claude, cursor, Windsurf) can seamlessly access the same memory repository, eliminating the need for duplicate input contexts

The open - source image product [**openmemory-mcp**]() ， provided in this project has pre installed the relevant runtime environment and provided deployment templates. Come and refer to the user guide to easily unlock the efficient experience of "out of the box use".

> **System requirements are as follows:**
>
> - CPU: 2GHz or higher
> - RAM: 4GB or larger
> - Disk: At least 40GB

## Prerequisites

[Register a Huawei account and activate Huawei Cloud](https://support.huaweicloud.com/usermanual-account/account_id_001.html)

## Image Description

| Image Specification                                          | Feature Description                                          | Remarks |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------- |
| [openmemory-mcp-v0.1.11-kunpeng](https://github.com/HuaweiCloudDeveloper/vllm-image/blob/openmemory-mcp-v0.1.11-kunpeng/README.md) | Installed and deployed based on Kunpeng servers + Huawei Cloud EulerOS 2.0 64bit |         |

## Get Help

- For more questions, you can contact us via [issue](https://github.com/HuaweiCloudDeveloper/neo4j-image/issues) or the service support of the specified product in the Huawei Cloud Marketplace.
- For other open - source images, see [open - source - image - repos](https://github.com/HuaweiCloudDeveloper/open - source - image - repos)

## How to Contribute

- Fork this repository and submit a merge request.
- Synchronously update README.md based on your open - source image information.
