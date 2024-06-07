---
topic: llm-app # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 大模型应用开发日报-2024-06-07
toc: true
menu_id: topic
date: 2024-06-07
tags: [大模型应用开发日报,开源项目]
categories: [大模型应用开发日报]
description: 
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/0c8bef0cc992ec63ab4bdeac48d4bf651379a5a1101e3e4e112c42c1bef57b24.jpg
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/0c8bef0cc992ec63ab4bdeac48d4bf651379a5a1101e3e4e112c42c1bef57b24.jpg
---
## 开源项目推荐

[**julep** 链接](https://github.com/julep-ai/julep)


## 技术介绍

[REWOO框架Reasoning without Observation](https://arxiv.org/abs/2305.18323)
- [langchain实现](https://github.com/langchain-ai/langgraph/blob/main/examples/rewoo/rewoo.ipynb)
- [LLM智能体的的生产之路:将推理和计划与行动和观察脱钩](https://medium.com/@raunak-jain/path-to-production-for-llm-agents-f0a9cafd2398)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240607183102.png)
[TDAG: A Multi-Agent Framework based on Dynamic Task Decomposition and Agent Generation](https://arxiv.org/abs/2402.10178)






## 开发经验
### 架构模式
- [大模型应用的 10 种架构模式](https://www.infoq.cn/article/idih2tuj1xyl3vxo16xb)
- [复合AI System(Conversational AI, CoPilots & RAG)的设计模式【英文版】](https://medium.com/@raunak-jain/design-patterns-for-compound-ai-systems-copilot-rag-fa911c7a62e0)
  - [The Shift from Models to Compound AI Systems 从模型到复合人工智能系统的转变](https://bair.berkeley.edu/blog/2024/02/18/compound-ai-systems/)
- [Generative AI Design Patterns](https://htmlpreview.github.io/?https://github.com/lakshmanok/generative-ai-design-patterns/blob/main/catalog.html)
  - 还在初期，未正式化
[自主代理的三种人工智能设计模式](https://alexsniffin.medium.com/three-ai-design-patterns-of-autonomous-agents-8372b9402f7c)
- [多智能体系统构建生产级具有智能体性质的人工智能系统的5大模式](https://dr-arsanjani.medium.com/patterns-for-agentic-ai-in-multi-agent-systems-patterns-1-4-f4c952bfc123)
>基于智能体的系统（）通常涉及个单个 LLM 模型，该模型作为一个智能体，执行多项任务，做出决策，并通过 "工具"（如果是机器人，则为执行器）与环境互动（感知、知觉、行动）。LLM 可被视为一个具有各种能力的整体。
>多智能体系统MAS(Multi-agent system)从基于智能体的系统发展而来，引入多个专门的 LLM。每个 LLM 作为一个独立的智能体，具有特定的角色或专长。这些智能体相互协作、沟通并协调行动，以解决单个智能体无法有效处理的复杂问题设计。具有智能体性质的人工智能系统具有自主性、专业化、实时适应、协作和主动决策等特点，而 LLMs 则具有一般性和多功能性。

[Generative AI Design Patterns using LLM](https://webcache.googleusercontent.com/search?q=cache:https://medium.com/@itsmybestview/generative-ai-design-patterns-using-llm-01eca97d0a1c)

[Generative AI Design Patterns: A Comprehensive Guide](https://towardsdatascience.com/generative-ai-design-patterns-a-comprehensive-guide-41425a40d7d0)


### Agentic RAG
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240607182710.png)

- [深入探究 Agentic Retrieval Augmented Generation (A-RAG)](https://www.linkedin.com/pulse/deep-dive-agentic-retrieval-augmented-generation-a-rag-sai-panyam-22dlc/)
- [deeplearning视频课程:Building Agentic RAG with Llamaindex](https://learn.deeplearning.ai/courses/building-agentic-rag-with-llamaindex/lesson/1/introduction)

- [Agentic-RAG](https://www.leewayhertz.com/agentic-rag/)
>Agentic RAG 是一种增强版的 Retrieval-Augmented Generation（RAG）技术，它通过引入智能代理来提高问题回答的准确性和深度。这些代理能够进行多步骤推理、使用外部工具和适应性学习，从而更有效地处理复杂的信息检索和生成任务。

- [llamaindex Agentic_RAG](https://www.llamaindex.ai/blog/agentic-rag-with-llamaindex-2721b8a49ff6)
  - [源码](https://github.com/cobusgreyling/LlamaIndex/blob/d8902482a247c76c7902ded143a875d5580f072a/Agentic_RAG_Multi_Document_Agents-v1.ipynb)
    >智能体式RAG，即采用智能体方式实施 RAG，增加了 RAG 实施的弹性和智能性。它很好地诠释了多智能体协作。
这个架构是一个很好的参考框架，说明如何通过第二层较小的worker智能体来优化扩展智能体。
Agentic RAG 就是一个可控的、定义明确的自主智能体实施范例。
最受追捧的企业 LLM 实施类型之一是 RAG，Agentic RAG 是其自然发展。
很容易想象这种架构在组织中添加更多的子机器人如何发展和扩展。
  - [Agentic RAG with Llama-index | Router Query Engine ](https://medium.com/aimonks/agentic-rag-with-llama-index-router-query-engine-01-381e83a418af)
  - [Agentic RAG With Llama-index | Multi-step Reasoning Capability Over Multiple Documents ](https://ai.gopubby.com/agentic-rag-with-llama-index-multi-step-reasoning-capability-over-multiple-documents-04-bd25a72362ea)

- [Implementing Agentic RAG using Langchain](https://medium.com/the-ai-forum/implementing-agentic-rag-using-langchain-b22af7f6a3b5)


### Graph-RAG
- [Graph vs. Vector RAG — Benchmarking, Optimization Levers, and a Financial Analysis Example](https://medium.com/neo4j/graph-vs-vector-rag-benchmarking-optimization-levers-and-a-financial-analysis-example-001587219683)


## 其他
[Orchestrating agentic systems 编排智能体系统](https://medium.com/@raunak-jain/orchestrating-agentic-systems-eb945d305083)