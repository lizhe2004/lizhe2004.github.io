---
title: 信息检索的未来-Agentic RAG
 
date: 2024-12-25
tags: [人工智能, RAG, Agentic RAG]
categories: [人工智能]
description: 探索检索增强生成（RAG）向Agentic RAG 演进,通过结合AutoGen、LangGraph 和 CrewAI 等创新工具和技术，旨在构建智能、自主的系统，重新定义检索增强系统与数据交互和推理的方式。
banner: 
cover: 
author: 李大侠
breadcrumb: true
leftbar:
  - recent
  - related
  - tagcloud
rightbar:
  - ghuser
  - toc
---

## 导言 

本文是探索检索增强生成（RAG）向Agentic RAG 演进的系列文章。我们将指导大家使用 AutoGen、LangGraph 和 CrewAI 等创新工具实际实现 Agentic RAG。通过结合这些技术，我们旨在构建智能、自主的系统，重新定义检索增强系统与数据交互和推理的方式。

在这篇基础文章中，我们将探讨 RAG 是什么、它的局限性，以及如何通过 Agentic RAG 克服这些挑战，解锁前所未有的能力。在今后的文章中，我们将通过实际演示、基准测试和使用案例，将这一旅程推向高潮。

 
## 什么是 RAG？

检索-增强生成（RAG）将信息检索与生成式人工智能相结合，以产生具有高度信息的输出。这种混合模型在知识检索和生成式语言模型之间架起了一座桥梁，能够生成准确度更高、更贴近上下文语境的响应。

## RAG 工作原理：
 示意图：基本的 RAG 工作流程：

[User Query] --> [Retriever: External Knowledge Base] --> [Generator: Language Model] --> [Output]


- Retriever（检索器）：搜索外部知识库或文档存储库以检索相关信息。此步骤用来确保生成的回复是以事实数据为基础的。
- Generator（生成器）：将检索到的数据与 GPT 等人工智能模型的生成能力相结合，生成连贯且上下文丰富的输出结果。
- Knowledge Source（知识源）：作为检索的基础，通常包括数据库、文档存储库或索引语料库。

### 常见应用：

- QA问答：提供基于外部数据源的客观事实性答案。
- 摘要：从检索到的文档中生成摘要。
- 客户支持：为用户提供准确的、可感知理解上下文的响应 
 
Document Analysis: Offering insights based on specific queries.
文档分析：基于特定查询提供见解。

文件分析：根据特定查询提供见解。
RAG is widely adopted due to its ability to leverage external knowledge, making it a crucial tool for applications requiring up-to-date or domain-specific information.
RAG 广泛采用，因其能够利用外部知识，使其成为需要最新或特定领域信息的应用的必备工具。

RAG 能够利用外部知识，因此被广泛采用，对于需要最新信息或特定领域信息的应用程序来说，RAG 是一个重要工具。

Drawbacks of RAG
RAG 的缺点
While RAG has proven effective, it is not without limitations. These challenges hinder its application in more complex or dynamic scenarios:
虽然 RAG 已被证明有效，但它并非没有局限性。这些挑战阻碍了其在更复杂或动态场景中的应用：

尽管 RAG 已被证明是有效的，但它并非没有局限性。这些挑战阻碍了它在更复杂或动态场景中的应用：

Static Query-Response Model:
静态查询-响应模型：

静态查询-响应模型：

RAG systems are reactive and respond only to explicit prompts. They lack the ability to autonomously plan tasks or adapt workflows.
RAG 系统是反应性的，仅对明确的提示做出响应。它们缺乏自主规划任务或适应工作流程的能力。

RAG 系统是被动的，只对明确的提示做出反应。它们缺乏自主规划任务或调整工作流程的能力。
Limited Reasoning Capabilities:
有限推理能力：

推理能力有限：

Traditional RAG cannot synthesize insights from multiple retrieved documents effectively, limiting its ability to handle multi-turn interactions or complex reasoning tasks.
传统 RAG 无法有效地从多个检索到的文档中综合见解，限制了其处理多轮交互或复杂推理任务的能力。

传统的 RAG 无法从多个检索文档中有效地综合出见解，从而限制了其处理多轮交互或复杂推理任务的能力。
Pipeline Complexity:  管道复杂性：
管道复杂性：

Balancing retrieval precision and generative quality requires extensive tuning. Inadequate optimization can lead to irrelevant or low-quality outputs.
平衡检索精度和生成质量需要大量调整。优化不足可能导致输出不相关或质量低下。

平衡检索精度和生成质量需要大量的调整。如果优化不足，可能会导致不相关或低质量的输出。
Knowledge Dependency:
知识依赖性：

Outputs heavily rely on the quality and scope of the external knowledge base. Incomplete or outdated repositories can degrade performance.
输出高度依赖于外部知识库的质量和范围。不完整或过时的存储库会降低性能。

输出在很大程度上依赖于外部知识库的质量和范围。不完整或过时的知识库会降低性能。
These limitations make RAG less suitable for tasks requiring dynamic interaction, adaptive reasoning, or multi-step decision-making.
这些限制使得 RAG 在需要动态交互、适应性推理或多步骤决策的任务中不太适用。

这些局限性使得 RAG 不太适合需要动态交互、自适应推理或多步骤决策的任务。

if you like this article and want to show some love:
如果您喜欢这篇文章并想表达一些爱意：
Clap 50 times — each one helps more than you think! 👏
拍 50 次掌——每一次都比你想的更有帮助！👏

拍手 50 次 - 每一次的帮助都比你想象的要大！👏
Follow me here on Medium and subscribe for free to catch my latest posts. 🫶
关注我在 Medium 上的账号，免费订阅以获取我的最新文章。🫶

在 Medium 上关注我，免费订阅我的最新文章。🫶
Let’s connect on LinkedIn, check out my projects on GitHub, and stay in touch on Twitter!
让我们在领英上联系，查看我的 GitHub 项目，并在推特上保持联系！

让我们在 LinkedIn 上联系，在 GitHub 上查看我的项目，在 Twitter 上保持联系！
What is Agentic RAG?
什么是代理 RAG？
Agentic RAG is an evolution of the RAG framework that integrates autonomous, agent-based reasoning capabilities. By combining retrieval-augmented generation with intelligent agents, Agentic RAG transforms static systems into proactive, decision-making entities capable of dynamic interaction and multi-turn reasoning.
代理型 RAG 是 RAG 框架的进化，集成了基于代理的自主推理能力。通过结合检索增强生成与智能代理，代理型 RAG 将静态系统转变为主动的、决策实体，能够进行动态交互和多轮推理。

代理 RAG 是 RAG 框架的演进，它集成了自主的、基于代理的推理能力。通过将检索增强生成与智能代理相结合，Agentic RAG 将静态系统转变为能够进行动态交互和多轮推理的主动决策实体。

Key Features of Agentic RAG:
Agentic RAG 的主要功能：
Agentic RAG 的主要功能：
Flowchart: Agentic RAG Architecture
流程图：代理 RAG 架构

[User Query]
   |
   v
[Agentic Layer: Multi-Agent System]
   |
   +--> [Retriever: Knowledge Sources]
   |
   +--> [Generator: Language Models]
   |
   +--> [External APIs/Databases]
   |
   v
[Dynamic, Context-Aware Output]
Autonomy:
自主性：

Agents can autonomously plan and execute tasks, removing the need for constant human intervention.
代理可以自主规划和执行任务，无需持续的人工干预。

代理可以自主规划和执行任务，无需人工不断干预。
Context Awareness:
情境意识：

Maintains global context across interactions, ensuring consistency and relevance in outputs.
维护交互中的全球上下文，确保输出的一致性和相关性。

在各种互动中保持全球背景，确保产出的一致性和相关性。
Proactive Reasoning:
主动推理：

Capable of multi-step reasoning, synthesizing information from multiple retrieved documents to form coherent and actionable insights.
具有多步推理能力，能够从多个检索到的文档中综合信息，形成连贯且可执行的见解。

能够进行多步推理，综合多个检索文件中的信息，形成连贯、可行的见解。
Dynamic Interaction:  动态交互：
动态互动：

Agents can interact with APIs, databases, and external systems in real-time, enabling updates to knowledge and adaptive workflows.
代理可以实时与 API、数据库和外部系统交互，实现知识的更新和自适应工作流程。

代理可以与应用程序接口、数据库和外部系统实时交互，实现知识更新和自适应工作流程。
Transformational Impact:
变革性影响：
Agentic RAG elevates traditional RAG systems into intelligent platforms suitable for complex applications such as autonomous research assistants, interactive knowledge bases, and dynamic customer support systems.
代理 RAG 将传统 RAG 系统提升为适用于复杂应用，如自主研究助手、交互式知识库和动态客户支持系统的智能平台。

代理 RAG 将传统的 RAG 系统提升为智能平台，适用于复杂的应用，如自主研究助理、交互式知识库和动态客户支持系统。

Why Agentic RAG?
为什么选择代理 RAG？
Agentic RAG addresses the limitations of traditional RAG and introduces groundbreaking capabilities that are essential for modern AI-driven systems.
代理 RAG 解决了传统 RAG 的局限性，并引入了现代 AI 驱动系统所必需的突破性功能。

Agentic RAG 解决了传统 RAG 的局限性，并引入了对现代人工智能驱动系统至关重要的开创性功能。

Enhanced Reasoning:
增强推理能力：
Agentic RAG supports multi-turn reasoning, allowing it to handle complex queries and synthesize insights across diverse knowledge domains. This capability is especially critical for applications like academic research and enterprise-level analytics.
代理 RAG 支持多轮推理，允许其处理复杂查询并跨不同知识领域综合洞察。此功能对于学术研究和企业级分析等应用尤为重要。

Agentic RAG 支持多轮推理，能够处理复杂的查询并综合不同知识领域的见解。这种能力对于学术研究和企业级分析等应用尤为重要。

Task Automation:
任务自动化：
By introducing autonomous agents, Agentic RAG can manage multi-step workflows, automating tasks such as report generation, multi-document analysis, and process optimization.
通过引入自主代理，Agentic RAG 可以管理多步骤工作流程，自动化报告生成、多文档分析和流程优化等任务。

通过引入自主代理，Agentic RAG 可以管理多步骤工作流程，自动执行报告生成、多文档分析和流程优化等任务。

Real-Time Adaptability:
实时适应性：
实时适应性：实时适应性：
Agentic RAG dynamically updates its context and knowledge base, making it highly adaptable to changing requirements or real-time data inputs.
代理 RAG 动态更新其上下文和知识库，使其高度适应变化的需求或实时数据输入。

Agentic RAG 可动态更新其上下文和知识库，使其高度适应不断变化的要求或实时数据输入。

Scalability for Complex Applications:
复杂应用的可扩展性
Unlike static RAG systems, Agentic RAG scales seamlessly to handle diverse and intricate use cases, from managing enterprise knowledge to supporting dynamic conversational agents.
与静态 RAG 系统不同，Agentic RAG 能够无缝扩展以处理各种复杂用例，从管理企业知识到支持动态对话代理。

与静态 RAG 系统不同，Agentic RAG 可无缝扩展，以处理各种复杂的用例，从管理企业知识到支持动态对话代理。

Building Agentic RAG
建筑代理 RAG
In the upcoming articles, we will demonstrate how to construct an Agentic RAG system using the following tools:
在即将发表的文章中，我们将展示如何使用以下工具构建一个代理 RAG 系统：

在接下来的文章中，我们将演示如何使用以下工具构建一个代理 RAG 系统：

AutoGen:
自动生成

A framework for generating and orchestrating intelligent agents capable of autonomous reasoning and task execution.
一个用于生成和编排能够进行自主推理和任务执行智能代理的框架。

用于生成和协调能够自主推理和执行任务的智能代理的框架。
LangGraph:
LangGraph：

A tool for defining logical workflows, enabling agents to execute multi-step reasoning and manage dependencies across tasks.
一个用于定义逻辑工作流程的工具，使代理能够执行多步推理并管理任务间的依赖关系。

定义逻辑工作流的工具，使代理能够执行多步推理并管理跨任务的依赖关系。
CrewAI:
CrewAI：

A collaborative agent system that enables teams of agents to work together, enhancing scalability and efficiency.
协作代理系统，使代理团队能够协同工作，提高可扩展性和效率。

协作代理系统可使代理团队协同工作，提高可扩展性和效率。
Key Architectural Principles:
主要建筑原则
主要建筑原则
Diagram: Modular Architecture of Agentic RAG
图代理 RAG 模块化架构

[User Interface] --> [Agent Coordinator]
   |
   +--> [Retrieval Module] --> [Knowledge Sources]
   |
   +--> [Generation Module] --> [Language Models]
   |
   +--> [Reasoning Module] --> [Agent Collaboration]
Modular Design: Separate modules for retrieval, generation, and agentic reasoning ensure flexibility and maintainability.
模块化设计：检索、生成和代理推理的独立模块确保灵活性和可维护性。

模块化设计：独立的检索、生成和代理推理模块确保了灵活性和可维护性。
Dynamic Agent Orchestration: AutoGen facilitates the deployment of specialized agents for different tasks.
动态代理编排：AutoGen 简化了针对不同任务的专用代理的部署。

动态代理协调：AutoGen 可为不同任务部署专门的代理提供便利。
Workflow Management: LangGraph manages dependencies and ensures logical task execution.
工作流管理：LangGraph 管理依赖关系并确保逻辑任务执行。

工作流程管理：LangGraph 可管理依赖关系，确保任务的合理执行。
Collaborative Intelligence: CrewAI integrates multiple agents into a cohesive, cooperative framework.
协作智能：CrewAI 将多个智能体整合到一个协同、合作的框架中。

协作智能：CrewAI 将多个代理集成到一个有凝聚力的合作框架中。
Benchmarks and Expected Benefits
基准和预期效益
基准和预期效益
Preliminary benchmarks highlight the potential of Agentic RAG to outperform traditional RAG systems across key metrics:
初步基准测试突出了 Agentic RAG 在关键指标上超越传统 RAG 系统的潜力：

初步基准测试结果表明，Agentic RAG 在各项关键指标上都有可能优于传统的 RAG 系统：

Accuracy:  准确性：
准确性：

Up to 25% improvement in task-specific accuracy through enhanced reasoning and retrieval integration.
最高可达 25%的任务特定准确性提升，通过增强推理和检索集成实现。

通过增强推理和检索整合，任务特定准确率最高可提高 25%。
Efficiency:
效率：

Faster response times for multi-turn interactions and dynamic workflows.
更快的响应时间，适用于多轮交互和动态工作流程。

多轮交互和动态工作流程的响应速度更快。
Scalability:
可扩展性：

Seamlessly handles complex, large-scale applications requiring diverse capabilities.
无缝处理需要多样化能力的复杂、大规模应用程序。

无缝处理需要不同功能的复杂、大规模应用。
Adaptability:
适应性强：

Real-time updates and dynamic context management make Agentic RAG suitable for rapidly evolving domains.
实时更新和动态上下文管理使 Agentic RAG 适用于快速发展的领域。

实时更新和动态上下文管理使 Agentic RAG 适用于快速发展的领域。

Image By Author  图片由作者提供
图片作者
Future Directions
未来发展方向
This article lays the groundwork for understanding Agentic RAG. In future installments, we will:
本文为理解代理 RAG 奠定基础。在未来的连载中，我们将：

本文为了解代理 RAG 奠定了基础。在今后的文章中，我们将

Explore Implementation:
探索实施：

Provide step-by-step guides for building Agentic RAG systems using AutoGen, LangGraph, and CrewAI.
提供使用 AutoGen、LangGraph 和 CrewAI 构建 Agentic RAG 系统的分步指南。

提供使用 AutoGen、LangGraph 和 CrewAI 构建 Agentic RAG 系统的分步指南。
Showcase Use Cases:
展示使用案例：

Demonstrate real-world applications, including autonomous research assistants, enterprise knowledge systems, and adaptive conversational agents.
展示现实世界的应用，包括自主研究助手、企业知识系统和自适应对话代理。

展示现实世界中的应用，包括自主研究助理、企业知识系统和自适应对话代理。
Measure Performance:
衡量绩效：

Present detailed benchmarks and performance analyses across various scenarios.
提供各种场景下的详细基准和性能分析。

提出各种方案的详细基准和性能分析。
Extend Capabilities:
扩展能力：

Discuss future enhancements, such as integrating advanced reasoning models or domain-specific adaptations.
讨论未来增强功能，例如集成高级推理模型或特定领域的适应性调整。

讨论未来的增强功能，如整合高级推理模型或特定领域的适应性。
By the end of this series, you will have the knowledge and tools to build cutting-edge Agentic RAG systems capable of addressing the most demanding AI challenges.
到本系列结束时，您将具备构建能够应对最苛刻人工智能挑战的尖端 Agentic RAG 系统的知识和工具。

在本系列课程结束时，您将掌握构建尖端 Agentic RAG 系统的知识和工具，从而能够应对最严峻的人工智能挑战。

Ollama-OCR: Now Available as a Python Package!
Ollama-OCR：现在作为 Python 包可用！
Stuck behind a paywall? Read for Free!
付费墙挡住了您？免费阅读！
medium.com

Let’s Built an AI-Powered Notepad from Scratch:
从零开始构建一个 AI 驱动的记事本：
Stuck behind a paywall? Read for Free!
付费墙挡住了您？免费阅读！
python.plainenglish.io

Conclusion
结论
Agentic RAG represents a significant leap forward in the field of information retrieval and AI-driven reasoning. By integrating autonomy, advanced reasoning, and dynamic adaptability, it opens up new possibilities for applications across industries. This article serves as the foundation of a journey into the practical development of Agentic RAG, laying the groundwork for future articles where we will implement these concepts using cutting-edge tools like AutoGen, LangGraph, and CrewAI.
代理 RAG 代表了信息检索和 AI 驱动推理领域的一大飞跃。通过整合自主性、高级推理和动态适应性，它为跨行业应用开辟了新的可能性。本文是探索代理 RAG 实际开发基础的旅程的起点，为未来文章奠定基础，在这些文章中，我们将使用 AutoGen、LangGraph 和 CrewAI 等尖端工具实现这些概念。

代理 RAG 代表着信息检索和人工智能驱动推理领域的一次重大飞跃。通过整合自主性、高级推理和动态适应性，它为各行各业的应用开辟了新的可能性。本文将作为 Agentic RAG 实际开发之旅的基础，为未来的文章奠定基础，我们将在未来的文章中使用 AutoGen、LangGraph 和 CrewAI 等尖端工具来实现这些概念。

As we progress through this series, we aim to demonstrate how Agentic RAG can solve real-world problems, set new benchmarks in AI performance, and transform traditional systems into intelligent, proactive entities. Stay tuned as we dive deeper into building and refining this transformative technology.
随着我们进入本系列的深入，我们旨在展示 Agentic RAG 如何解决现实世界问题，在 AI 性能上设定新基准，并将传统系统转变为智能、主动的实体。敬请关注，我们将进一步探讨和改进这项变革性技术。

随着本系列的深入，我们将展示 Agentic RAG 如何解决现实世界中的问题，如何设定人工智能性能的新基准，以及如何将传统系统转变为智能、主动的实体。敬请期待我们对这一变革性技术的深入构建和完善。

Additional Resource: