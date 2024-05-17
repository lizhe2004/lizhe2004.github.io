---
title: 高级RAG之Adaptive-RAG框架的原理和内部实现
toc: true
date: 2024-05-16
tags: [Adaptive-RAG,大模型,RAG,检索增强生成]
categories: [人工智能]
description: 一篇文章让你了解Adaptive-RAG框架的原理和内部,通过自我反思和评估来更精准地检索和文本生成
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

[论文](https://arxiv.org/abs/2403.14403)  
作者: [https://twitter.com/SoyeongJeong97](https://twitter.com/SoyeongJeong97)

参考实现
[llamaindex实现版](https://github.com/mistralai/cookbook/blob/main/third_party/LlamaIndex/Adaptive_RAG.ipynb)
	- 大致对标于[Roouter](https://docs.llamaindex.ai/en/stable/module_guides/querying/router/?h=router)的概念和实现的功能
[langchain实现版：Adaptive RAG Cohere Command R](https://github.com/langchain-ai/langgraph/blob/main/examples/rag/langgraph_adaptive_rag_cohere.ipynb)
[langchain版：A ReAct agent with Command R+, achieving the same goals as Adaptive RAG](https://github.com/cohere-ai/notebooks/blob/main/notebooks/react_agent_adaptive_rag_cohere.ipynb)