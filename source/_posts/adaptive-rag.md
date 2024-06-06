---
title: 高级RAG之Adaptive-RAG框架的原理和内部实现
toc: true
date: 2024-05-16
tags: [Adaptive-RAG,大模型,RAG,检索增强生成]
categories: [人工智能]
description: 一篇文章让你了解Adaptive-RAG框架的原理和内部,通过自我反思和评估来更精准地检索和文本生成
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240522170854.png
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240522170854.png
author: 李大侠
breadcrumb: true
leftbar:
  - recent
  - related
  - tagcloud
rightbar:
  - toc
---

[论文](https://arxiv.org/abs/2403.14403)  
作者: [https://twitter.com/SoyeongJeong97](https://twitter.com/SoyeongJeong97)
[Github地址：](https://github.com/starsuzi/Adaptive-RAG)

## 背景
现有的检索增强型LLMs方法在处理不同复杂度的查询时，要么对于简单查询过于复杂，造成不必要的计算开销，要么对于复杂查询的处理不够充分。鉴于此，研究者们提出了Adaptive-RAG框架，旨在根据查询的复杂度动态选择最合适的策略，以实现在简单查询和复杂查询之间的平衡。Adaptive-RAG的目标是在保持高准确性的同时，尽可能减少计算资源的消耗。通过自适应选择最合适的检索策略，框架能够在处理简单查询时避免不必要的计算开销，而在处理复杂查询时提供充分的信息支持。

## 核心逻辑
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240522170854.png)
1、查询复杂度评估
Adaptive-RAG使用一个小型的语言模型作为分类器，该分类器的任务是预测输入查询的复杂度级别。分类器有三个输出类别：简单（A）、中等（B）和复杂（C），分别对应不同的检索策略。这个分类器通过自动收集的标签来训练。标签的获取有两种方式： 
  - 基于模型预测结果的自动标注：分类器的训练数据是通过自动标注获得的。对于每个查询，框架会使用三种不同的检索增强型LLM策略（无检索、单步检索和多步检索）进行处理，并根据这些策略的预测结果来确定查询的复杂度标签。
    - 如果非检索方法能够正确生成答案，则对应问题的标签为简单（A）；
    - 如果单步检索方法和多步检索方法都能正确回答，而非检索方法失败，则对应问题的标签为中等（B）；
    - 如果只有多步检索方法能够正确回答，则对应问题的标签为复杂（C）
  - 基于数据集中固有的归纳偏差：除了基于模型预测的标注外，框架还利用数据集中的固有偏差来进行标注。
    - 单步问答数据集中的查询通常适合使用单步检索策略
    - 多步问答数据集中的查询则更适合使用多步检索策略。
2、策略选择与执行
根据分类器的输出，框架将动态选择相应的检索策略。
非检索方法（No Retrieval）：对于被分类器标记为简单的查询（A），Adaptive-RAG直接使用LLM生成答案，不进行外部知识检索。这种方法适用于那些模型已经知道答案的简单问题，不需要额外的外部信息。
单步检索方法（Single-step Approach）：对于中等复杂度的查询（B），框架会先从外部知识源检索一次相关信息，然后将检索到的文档作为上下文信息输入到LLM中，帮助模型生成更准确的答案。
多步检索方法（Multi-step Approach）：对于复杂的查询（C），Adaptive-RAG采用迭代的方式，多次访问检索器和LLM，通过Chain-of-Thought推理和文档检索相结合的方式，逐步构建答案。

3、效率与准确性的平衡
- 自适应调整：Adaptive-RAG的核心优势在于能够根据查询的实际复杂度自适应地调整检索策略，从而在保持高准确性的同时，减少不必要的计算开销。
- 无缝切换：由于LLM和检索器的操作对于不同的输入是一致的，Adaptive-RAG能够在不同复杂度的查询之间无缝切换，无需改变模型架构或参数。


参考实现
[llamaindex实现版](https://github.com/mistralai/cookbook/blob/main/third_party/LlamaIndex/Adaptive_RAG.ipynb)
	- 大致对标于[Roouter](https://docs.llamaindex.ai/en/stable/module_guides/querying/router/?h=router)的概念和实现的功能
	- 通过引入RouterQueryEngine和FunctionCalling能力来根据查询请求的复杂度调用不同的工具或索引。
    - 复杂查询：将利用多种工具，需要从多个文档中获取上下文信息。(代码中的需要多次检索的agent “What did Lyft do in R&D in 2022 vs 2020?”)
    - 简单查询：将只使用单个工具，需要从单个文档中获取上下文信息  （代码中的大模型直接生成答案["What is the capital of France?"]和单次检索["What did Lyft do in R&D in 2020?"]）
[langchain实现版：Adaptive RAG Cohere Command R](https://github.com/langchain-ai/langgraph/blob/main/examples/rag/langgraph_adaptive_rag_cohere.ipynb)
  -  融合了query analysis和 active / self-corrective RAG 两方面的技术。
  -  执行query analysis按下面三种情况进行路由选择：
     -  No Retrieval (LLM answers)
     -  Web-search
     -  Iterative RAG
[langchain版：A ReAct agent with Command R+, achieving the same goals as Adaptive RAG](https://github.com/cohere-ai/notebooks/blob/main/notebooks/react_agent_adaptive_rag_cohere.ipynb)