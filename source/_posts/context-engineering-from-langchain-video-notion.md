---
title: 智能体的上下文工程（翻译自langchain的视频分享的文字内容）
toc: true
date: 2025-07-09
tags: [Context Engineering,上下文工程,大模型,Agent,智能体]
categories: [人工智能]
description: langchain 关于Context Engineering的理解和介绍，主要包括上下文工程的定义、构成要素以及技术策略
banner: https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707154223.png
cover: https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707154223.png
author: 李大侠
breadcrumb: true
leftbar:
  - recent
  - related
  - tagcloud
rightbar:
  - toc
---
原文 链接：https://mirror-feeling-d80.notion.site/Context-Engineering-for-Agents-21f808527b17802db4b1c84a068a0976
## 上下文工程
- 智能体需要上下文（例如，指令、外部知识、工具反馈）来执行任务。

> 上下文工程是一门艺术和科学，它在代理轨迹的每一步中，用最恰当的信息填充上下文窗口。
- 常见策略：
  - 写入上下文 - 将其保存在上下文窗口之外，以帮助代理执行任务。
  - 选择上下文 - 将其拉入上下文窗口，以帮助代理执行任务。
  - 压缩上下文 - 只保留执行任务所需的令牌。
  - 隔离上下文 - 将其拆分以帮助代理执行任务。
LangGraph 旨在支持这些策略。
![20250707155913](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707155913.png)
## 上下文工程定义
![20250707155959](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707155959.png)
![20250707160035](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707160035.png)
https://x.com/tobi/status/1935533422589399127
https://x.com/karpathy/status/1937902205765607626

[Harrison Chase The rise of "context engineering"](https://blog.langchain.com/the-rise-of-context-engineering/)

## 定义

> “上下文工程是‘……为下一步用最恰当的信息填充上下文窗口的精妙艺术和科学。’”

## 类比
[Karpathy](https://www.youtube.com/watch?v=LCEmiRjPEtQ)：LLM 是一种新型操作系统
LLM 是 CPU
上下文窗口是 RAM 或“工作内存”，其处理上下文的[能力有限](https://lilianweng.github.io/posts/2023-06-23-agent/)
管理什么信息适合 RAM 类似于上面提到的“上下文工程”
![20250707160536](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707160536.png)
## 上下文类型
一个涵盖几种不同类型上下文的[伞形学科](https://x.com/dexhorthy/status/1933283008863482067)：

指令 – 提示、记忆、少样本示例、工具描述等

知识 – 事实、记忆等

工具 – 工具调用反馈
![20250707160848](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707160848.png)


## 为什么这对智能体来说更难
- 长期运行的任务和累积工具调用反馈
- 智能体通常会使用大量令牌！
![20250707162647](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707162647.png)
![20250707162656](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707162656.png)
- Drew Breunig 很好地[罗列](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html)了更长上下文的导致的失败问题：
  - 上下文中毒（Context Poisoning）：幻觉内容添加到上下文
  - 上下文干扰(Context Distraction)：上下文信息过多导致淹没模型训练内容
  - 上下文混淆(Context Confusion)：多余的上下文影响响应时
  = 上下文冲突(Context Clash)：上下文的某些部分不一致

- 上下文工程在构建智能体时至关重要！

Cognition Cognition | [Don’t Build Multi-Agents](https://cognition.ai/blog/dont-build-multi-agents)
>  Context Engineering is effectively the #1 job of engineers building AI agents.
上下文工程实际上是构建 AI 代理的工程师的头号任务。

## 方法
- 上下文写入意味着将其保存在上下文窗口之外，以帮助代理执行任务。
- 上下文选择意味着将其拉入上下文窗口，以帮助代理执行任务。
- 上下文压缩涉及只保留执行任务所需的token。
- 上下文隔离涉及将上下文拆分以帮助代理执行任务。
![20250707163001](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707163001.png)
## 写入
- 上下文写入意味着将其保存在上下文窗口之外，以帮助代理执行任务。
- 当人类解决任务时，我们会做笔记并记住未来的相关任务。
- 笔记 → 暂存区
- 记住 → 记忆

### 暂存区
- 在代理执行任务时保留信息
- [Anthropic 的 multi-agent researcher](https://www.anthropic.com/engineering/built-multi-agent-research-system)
> LeadResearcher 首先思考方案并将其计划方案保存到记忆中以保留上下文，因为如果上下文窗口超过 200,000 个令牌，它将被截断，并且保留计划很重要。
使用运行时[状态 state 对象](https://langchain-ai.github.io/langgraph/concepts/low_level/#state)或文件。

### 记忆
- [生成式代理](https://ar5iv.labs.arxiv.org/html/2304.03442)从z之前的代理反馈集合中合成记忆
- [ChatGPT](https://help.openai.com/en/articles/8590148-memory-faq)、[Cursor](https://forum.cursor.com/t/0-51-memories-feature/98509) 和 [Windsurf](https://docs.windsurf.com/windsurf/cascade/memories) 都自动生成记忆。

![20250707163843](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707163843.png)
### 选择
- 上下文选择指的是将其拉入上下文窗口以帮助代理执行任务。

### 暂存区
- 工具调用
- 从状态读取

### 记忆
- 少样本示例（情景记忆 ([episodic](https://langchain-ai.github.io/langgraph/concepts/memory/#memory-types) [memories](https://arxiv.org/pdf/2309.02427))）用于所需行为的示例
- 指令（程序记忆 ( [procedural](https://langchain-ai.github.io/langgraph/concepts/memory/#memory-types)  [memories](https://arxiv.org/pdf/2309.02427)) ）用于引导行为
- 事实（语义记忆 ([semantic](https://langchain-ai.github.io/langgraph/concepts/memory/#memory-types) [memories](https://arxiv.org/pdf/2309.02427))  
![20250707164415](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707164415.png)
- 指令 → 规则文件 / CLAUDE.md
- 事实 → 集合

### 工具
- 基于工具描述的 RAG：最近的[论文](https://arxiv.org/abs/2505.03275)表明这可以提高3倍的选择效率。

### 知识
- RAG 是一个大话题
- 代码智能体一些大型 RAG 应用程序
https://x.com/_mohansolo/status/1899630246862966837
![20250707165905](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707165905.png)
## 压缩
- 上下文压缩涉及只保留执行任务所需的token。

### 总结
- Claude Code “自动压缩” [Anthropic Manage costs effectively](https://docs.anthropic.com/en/docs/claude-code/costs)
- 已完成的工作区  [Anthropic AI： How we built our multi-agent research system](https://www.anthropic.com/engineering/built-multi-agent-research-system)
将上下文传递给线性子代理 [Cognition | Don’t Build Multi-Agents](https://cognition.ai/blog/dont-build-multi-agents)
![20250707172107](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707172107.png)

### 修剪
- 启发式：最近的消息
- 学习
Provence: efficient and robust context pruning for retrieval-augmented generation](https://arxiv.org/abs/2501.16214)

## 隔离
- 上下文隔离指的是将其拆分以帮助代理执行任务。

### 多智能体
- [Swarm](https://github.com/openai/swarm) “关注点分离”原则，每个智能体都有自己的上下文
- [Anthropic AI： How we built our multi-agent research system](https://www.anthropic.com/engineering/built-multi-agent-research-system)

> [Subagents operate] in parallel with their own context windows, exploring different aspects of the question simultaneously. 

> [子智能体]在各自的上下文窗口中并行运行，，同时探索问题的不同方面。

![20250707172716](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707172716.png)

### 环境


[huggingface Open-source DeepResearch – Freeing our search agents](https://huggingface.co/blog/open-deep-research#:~:text=From%20building%20,it%20can%20still%20use%20it)

![20250707172724](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707172724.png)

### 状态  State
- [State Models定义](https://docs.pydantic.dev/latest/concepts/models/)
状态对象：https://langchain-ai.github.io/langgraph/concepts/low_level/#state 定义图模式


## 上下文工程 + LangGraph
### Tracing + Eval (链路追踪和评估)
- [langsmith 入门](https://docs.smith.langchain.com/)
### 写入
#### 暂存区
- [检查点机制（Checkpointing)](https://langchain-ai.github.io/langgraph/concepts/persistence/)以在会话中保留[智能体状态](https://langchain-ai.github.io/langgraph/concepts/low_level/#state)
#### 记忆
- [长期记忆](https://langchain-ai.github.io/langgraph/concepts/memory/#long-term-memory)以在多个会话中保留上下文

### 选择
#### 暂存区
- 在任何节点中检索状态 State
#### 记忆
- 在任何节点中检索[长期记忆](https://langchain-ai.github.io/langgraph/concepts/memory/#long-term-memory)
- [deeplearningai_ Long-Term Agentic Memory with LangGraph](https://www.deeplearning.ai/short-courses/long-term-agentic-memory-with-langgraph/)
- [LangChain Academy Building Ambient Agents with LangGraph](https://academy.langchain.com/courses/ambient-agents)
![20250707173811](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250707173811.png)
#### 工具
- [langgraph-bigtool](https://github.com/langchain-ai/langgraph-bigtool)

#### 知识
- [Agentic RAG](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_agentic_rag/)

### 压缩
#### 总结 + 修剪
- 总结、修剪消息历史：https://langchain-ai.github.io/langgraph/how-tos/memory/add-memory/#manage-short-term-memory
- [低级框架](https://blog.langchain.com/how-to-think-about-agent-frameworks/)，提供了在节点内定义逻辑的灵活性
  - 后处理工具执行：https://github.com/langchain-ai/open_deep_research/blob/e5a5160a398a3699857d00d8569cb7fd0ac48a4f/src/open_deep_research/utils.py#L1407

### 隔离
#### 多智能体
- [langgraph-swarm-py](https://github.com/langchain-ai/langgraph-swarm-py)
- [LangChain Conceptual Guide: Multi Agent Architectures](https://www.youtube.com/watch?v=4nZl32FwU-o)
- [LangChain Multi-agent swarms with LangGraph](https://www.youtube.com/watch?v=JeyDrn1dSUQ)
- [LangChain Hierarchical multi-agent systems with LangGraph](https://www.youtube.com/watch?v=B_0TNuYi56w)
#### 环境
- [LangGraph + E2B](https://github.com/jacoblee93/mini-chat-langchain?tab=readme-ov-file) 
- Pyodide [LangChain LangChain Sandbox: Run Untrusted Python Safely for AI Agents](https://www.youtube.com/watch?v=FBnER2sxt0w)
#### 状态
状态对象(State object）: [Overview Define graph schema](https://langchain-ai.github.io/langgraph/concepts/low_level/#state)

## 总结
- 上下文写入意味着将其保存在上下文窗口之外，以帮助代理执行任务。
- 上下文选择意味着将其拉入上下文窗口，以帮助代理执行任务。
- 上下文压缩涉及只保留执行任务所需的令牌。
- 上下文隔离涉及将其拆分以帮助代理执行任务。
![20250709103436](https://cdn.jsdmirror.com/gh/lizhe2004/pic-repo@master//imgs/20250709103436.png)