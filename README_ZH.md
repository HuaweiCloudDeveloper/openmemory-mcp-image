## 目录

- [仓库简介](#项目介绍)
- [前置条件](#前置条件)
- [镜像说明](#镜像说明)
- [获取帮助](#获取帮助)
- [如何贡献](#如何贡献)

## 项目介绍

[openmemory-mcp](https://github.com/mem0ai/mem0/tree/main/openmemory) OpenMemory 是您的 LLM 个人记忆层，私有、可移植且开源。您的记忆存储在本地，让您完全掌控自己的数据。使用个性化记忆构建 AI 应用程序，同时确保数据安全。

### **核心功能：**

- **跨会话记忆存储**：

​    支持任意文本块的长期保存与调用，使 AI 在每次交互中都能“记住”之前的内容，无需从零开始



- **智能检索机制**：

​       借助 Qdrant 向量数据库，实现基于语义相关性的高效检索，超越传统关键字匹配的限制

- **完全本地部署**：

​      整个系统基于 Docker、PostgreSQL 和 Qdrant 构建，所有数据均在本地处理和存储，不会向外发送任何信息，保障隐私安全



**跨工具记忆共享**：支持 MCP 协议的客户端（如 Claude、Cursor、Windsurf）可以无缝访问同一记忆库，消除重复输入上下文的需要

本项目提供的开源镜像商品 [**openmemory-mcp**]() ，已预先安装相关运行环境，并提供部署模板。快来参照使用指南，轻松开启“开箱即用”的高效体验吧。

> **系统要求如下：**
>
> - CPU: 2GHz 或更高
> - RAM: 4GB 或更大
> - Disk: 至少 40GB

## 前置条件

[注册华为账号并开通华为云](https://support.huaweicloud.com/usermanual-account/account_id_001.html)

## 镜像说明

| 镜像规格                                                     | 特性说明                                                  | 备注 |
| ------------------------------------------------------------ | --------------------------------------------------------- | ---- |
| [openmemory-mcp-v0.1.11-鲲鹏](https://github.com/HuaweiCloudDeveloper/vllm-image/blob/openmemory-mcp-v0.1.11-kunpeng/README_ZH.md) | 基于 鲲鹏服务器 + Huawei Cloud EulerOS 2.0 64bit 安装部署 |      |

## 获取帮助

- 更多问题可通过 [issue](https://github.com/HuaweiCloudDeveloper/neo4j-image/issues) 或 华为云云商店指定商品的服务支持 与我们取得联系
- 其他开源镜像可看 [open-source-image-repos](https://github.com/HuaweiCloudDeveloper/open-source-image-repos)

## 如何贡献

- Fork 此存储库并提交合并请求
- 基于您的开源镜像信息同步更新 README.md
