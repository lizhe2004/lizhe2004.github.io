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

[**LangGPT** 链接](https://github.com/langgptai/LangGPT)
>LangGPT 项目旨在以结构化、模板化的方式编写高质量 ChatGPT prompt,维护了很多prompt教程、示例和模版等。

[Awesome-ChatTTS](https://github.com/libukai/Awesome-ChatTTS)
>整理和汇总了 ChatTTS 项目的常见问题和相关资源，是 ChatTTS 的最佳入门指南. ChatTTS是目前很火的一个TTS模型，不过由于训练数据存在版权问题，所以没法商用。

[STORM](https://github.com/stanford-oval/storm)
>STORM: Synthesis of Topic Outlines through Retrieval and Multi-perspective Question Asking。它根据互联网搜索从头开始编写类似维基百科的文章。
>将生成带有引用的长文章分为两个步骤：
>* 预写阶段：系统通过互联网进行研究，收集参考资料并生成大纲。
>* 写作阶段：系统使用大纲和参考文献生成带有引文的全文文章。
>
>STORM 认为研究过程自动化的核心是自动提出好的问题。直接提示语言模型提出问题效果并不好。为了提高问题的深度和广度，STORM 采用了两种策略：
>* 观点引导提问：给定输入主题，STORM 通过调查类似主题的现有文章来发现不同的观点，并使用它们来控制提问过程。
>* 模拟对话：STORM 模拟维基百科作者和基于互联网资源的主题专家之间的对话，使语言模型能够更新其对主题的理解并提出后续问题。
>
>基于两个阶段的分离，STORM使用dspy以高度模块化的方式实现。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240620190544.png)


[AntiFraudChatBot](https://github.com/Turing-Project/AntiFraudChatBot)
>AntiFraudChatBot是基于大规模预训练中文模型、语义识别与检测、对话意图等技术所构建的生成式对话QA框架，目前第一版模型针对反诈骗的场景化任务，对比传统的BertQA模型或non-prompt模型，在真实测试中AI对话的流畅度有明显提高。
## 技术介绍

[REWOO框架Reasoning without Observation](https://arxiv.org/abs/2305.18323)
- [langchain实现](https://github.com/langchain-ai/langgraph/blob/main/examples/rewoo/rewoo.ipynb)
- [LLM智能体的的生产之路:将推理和计划与行动和观察脱钩](https://medium.com/@raunak-jain/path-to-production-for-llm-agents-f0a9cafd2398)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240607183102.png)
[TDAG: A Multi-Agent Framework based on Dynamic Task Decomposition and Agent Generation](https://arxiv.org/abs/2402.10178)


[Youtube视频：Llamaindex Vs Langchain Framework](https://www.youtube.com/watch?v=1eym7BTnuNg&ab_channel=KrishNaik)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611190250.png)

吴恩达关于agenticflow的视频分享
- [What's next for AI agentic workflows ft](https://www.youtube.com/watch?v=sal78ACtGTc) 
- [Andrew Ng On AI Agentic Workflows And Their Potential For Driving AI Progress](https://www.youtube.com/watch?v=q1XFm21I-VQ) 
  - [中文图文字版链接](https://www.36kr.com/p/2823792342620550)

Agentic设计模式
- [Agentic Design Patterns Part 1](https://www.deeplearning.ai/the-batch/how-agents-can-improve-llm-performance/)
  - 提高AI Agent的四种策略：
  - 反思：大模型检查自己的工作以提出改进的方法。
  - 使用工具：让大模型拥有网络搜索、代码执行或任何其他功能等工具来帮助其收集信息、采取行动或处理数据。
  - 规划：大模型提出并执行一个多步骤计划来实现目标（例如，撰写论文大纲，然后进行在线研究，然后撰写草稿，等等）。
  - 多智能体协作：多个人工智能智能体一起工作，分解任务并讨论和辩论想法，以提出比单个智能体更好的解决方案。
- [Agentic Design Patterns Part 2: Reflection](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-2-reflection/)
- [Agentic Design Patterns Part 3: Tool Use](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-3-tool-use/)
- [Agentic Design Patterns Part 4: Planning](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-4-planning/)
- [Agentic Design Patterns Part 5, Multi-Agent Collaboration](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-5-multi-agent-collaboration/)

- [What is Agentic Workflow? Discover How AI Enhances Productivity](https://masterdai.blog/exploring-agentic-workflows-a-deep-dive-into-ai-enhanced-productivity/)
- [Unlocking AI Potential: Exploring Agentic Workflows and Their Implications on Language Models | by Arvind kumar Vartiya | Medium](https://medium.com/@arvindkrvartiya/unlocking-ai-potential-exploring-agentic-workflows-and-their-implications-on-language-models-5f8015d878e7)
- [AI Agents, Agentic Workflows | AIGuys](https://webcache.googleusercontent.com/search?q=cache:https://medium.com/aiguys/next-for-llms-and-rag-ai-agentic-workflows-1869ba0a6796)

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
- [AI Agentic Design Patterns with AutoGen【吴恩达视频课程】](https://www.deeplearning.ai/short-courses/ai-agentic-design-patterns-with-autogen/)
  - 通过该课程可以学习如何构建和自定义多代理系统，使代理能够承担不同的角色并使用 AutoGen 协作完成复杂的任务，
  - AutoGen 是一个支持开发 LLM 的框架使用多代理的应用程序。



## 扩展阅读
[AI and the American Smile](https://medium.com/@socialcreature/ai-and-the-american-smile-76d23a0fbfaf)
探讨了人工智能生成图像中人物表情的文化差异及其意义。作者认为,由于训练数据集主要来自于美国文化,人工智能生成的图像将文化差异简单化,呈现出一种单一的"微笑"表情,这掩盖了不同文化背景下表情的多样性和内在含义。
美国人希望公众人物对他们微笑，以此强调社会秩序和平静。另一方面，俄罗斯人认为公职人员在公共场合保持庄严的表情是适当的，因为他们的行为应该反映出其工作的严肃性。美国重要公众人物露齿的“霸道微笑”激发了美国人的信心和承诺。相反，俄罗斯人期望领导人表情严厉，以表现出“严肃的意图、有效性和可靠性”。
一些文化中认为未来是不确定的，微笑——一种与自信相关的行为——是不可取的。俄罗斯文化在避免不确定性方面排名非常低，俄罗斯人对笑脸的智力评价明显低于其他文化。
来自政府腐败程度较高的国家的人们更有可能将笑脸视为不诚实。

![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/1_IXJmP8C4SxptcJzA4W1XDw.gif)

AI生成的美洲原住民战士的照片
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611100047.png)

真实的1865年美洲原住民酋长照片
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611100248.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611100727.png)

AI生成的古代波利尼西亚战士的自拍片
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611100802.png)

毛利人是新西兰（奥特罗亚）的土著波利尼西亚人民，他们真实的传统毛利战舞仪式照片
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611101042.png)

AI生成的摆出自拍姿势的苏联士兵
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611101146.png)

东欧士兵自拍的真实照片
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611101218.png)

AI 生成的二战美国海军军官自拍照图像
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611102359.png)
二战时期的美国海军军官真实招聘
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240611102417.png)

>2018 年，罗切斯特大学的研究人员进行了一项实验，旨在了解[欺骗与面部表情之间的关系](https://www.rochester.edu/newscenter/data-science-facial-expressions-who-if-lying-321252/)。参与者被分成描述者和询问者角色。描述者被展示了一张图像，并要求他尽可能详细地记住它。然后他们被指示向审问者说谎或真实描述他们刚刚看到的东西，而审问者并不知道给描述者的指示。在151对个体参与者之间的记录交流中，产生了130万帧面部表情。然后，研究人员使用机器学习自动寻找模式。在没有任何预先确定的标签或类别的情况下，结果识别出最常与说谎相关的表情：一个“高强度版本”的杜兴笑容——一个扩展到脸颊/眼睛和嘴巴肌肉的笑容（19世纪，杜兴在治疗一个因为肌营养不良导致面部表情丧失的病人时，发现用电刺激面部的相关肌肉收缩能够产生特定的表情。比如刺激眼角与颧骨附近的肌肉运动组合，便使病人产生了微笑的表情，此后这被称做“杜兴微笑”）。

阿拉巴马州斯普林希尔学院 (Spring Hill College) 教授理论、性别和跨文化交流的克里斯蒂娜·科切米多娃 (Christina Kotchemidova) 认为，紧张，痛苦，虚伪的狰狞表情——现代美国的微笑——源于 18 世纪的一场巨大的情感转变。但这也是建立在谎言之上的。他认为，在这种转变之前，美国的情感景观围绕着悲伤和忧郁等负面情绪，这些情绪被视为同情心和高尚的象征。受宗教改革前和早期欧洲基督教思想的启发，美国人和欧洲人都认为尘世的苦难是崇高的，并且是幸福来世所必需的。这一时期的文学、视觉艺术和戏剧旨在激发悲伤，在欧洲，当众哭泣是司空见惯的事。
启蒙时代将文化推向了不同的方向。当思想家和艺术家接受理性时，他们也开始相信，在我们的尘世生活和来世，幸福是可以被允许的。悲伤的文化开始被快乐的文化所取代，这反过来又影响了阶级结构的变化。新兴中产阶级将管理情绪的能力视为其身份的关键。生意失败和疾病与情绪控制失败有关，而快乐与繁荣有关。最终，性格开朗成为就业的先决条件。


 “面部‘表情’的概念意味着一种通过一系列面部动作寻求释放的内在感觉。 在将全球各种文明的面部表情多样性简化为一种单一、统一的视角时，AI将历史、文化、摄影和情感概念的广泛范围塌缩在一起。它呈现了一种关于某种普遍性的虚假视觉叙事，而在现实世界中——真实的人类在这里生活并创造了文化、表达和意义已经有几十万年的历史——这些都绝不是统一的。
