---
topic: llm-app # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 大模型应用开发日报-2024-08-12
toc: true
menu_id: topic
date: 2024-08-22
tags: [大模型应用开发日报,开源项目]
categories: [大模型应用开发日报]
description: 
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/ec648ab7259325c3f39f0e209b927e8e11e85f9baba85312cb2932eb9a92b48e.jpg
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/ec648ab7259325c3f39f0e209b927e8e11e85f9baba85312cb2932eb9a92b48e.jpg
---



## 开源项目推荐
- [Indexify](https://github.com/tensorlakeai/indexify)
>Indexify 是一个开源引擎，用于使用可重复使用的提取器进行嵌入、转换和特征提取，为非结构化数据（视频、音频、图像和文档）快速构建数据流水线。当；流水线生成嵌入或结构化数据时，Indexify 会自动更新向量数据库、结构化数据库 (Postgres)。

- [kotaemon](https://github.com/Cinnamon/kotaemon)
>kotaemon 是一个开源的、基于 RAG (Retrieval-Augmented Generation) 的文档问答工具,主要特点包括:
>- 提供简洁美观的用户界面,支持多用户登录、文档集合管理、对话分享等功能。
>- 支持多种本地和云端 LLM 及 Embedding 模型,如 OpenAI、Azure、Ollama 等。
>- 使用混合检索管道,结合全文和向量检索,并进行重排序,以确保最佳的检索质量。
>- 支持包含图表的多模态文档解析和问答。
>- 提供带文档预览的高级引用功能,直接在浏览器内的 PDF 阅读器中突出显示相关内容。
>- 支持复杂推理方法,如问题分解、基于 agent 的推理(如 ReAct、ReWOO)等。
>- 在界面上提供可配置的检索和生成设置(包括 prompt)。
>- 基于 Gradio 构建,UI 元素可灵活定制,并支持多种文档索引和检索策略。

- [RAGLAB](https://github.com/fate-ubw/raglab)
>RAGLAB是一个模块化、面向研究的开源框架,用于检索增强型生成(Retrieval-Augmented Generation, RAG)算法。它提供了6种现有RAG算法的复制,以及一个全面的评估系统,包括10个基准数据集,使得RAG算法之间的公平比较和新算法、数据集和评估指标的高效开发成为可能。
>主要功能点
>- 全面的RAG生态系统:支持从数据收集和训练到自动评估的整个RAG流程。
>- 先进的算法实现:复制6种最先进的RAG算法,并提供易于扩展的框架来开发新算法。
>- 交互模式和评估模式:交互模式专门设计用于快速理解算法,评估模式专门设计用于复制论文结果和科学研究。
>- 公平比较平台:在5种任务类型和10个数据集上提供6种算法的基准结果。
>- 高效的检索客户端:提供本地API,支持并行访问和缓存,平均延迟低于1秒。
>- 多样化的生成器支持:兼容70B+模型、VLLM和量化技术。
>- 灵活的指令实验室:可定制的指令模板,适用于各种RAG场景。

## 技术介绍

## 扩展阅读
- [论文：Graph Retrieval-Augmented Generation: A Survey](https://arxiv.org/pdf/2408.08921)
- [anthropic的系统提示词分享](https://docs.anthropic.com/en/release-notes/system-prompts#july-12th-2024)