---
topic: llm-app # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 大模型应用开发日报-2024-09-03
toc: true
menu_id: topic
date: 2024-09-03
tags: [大模型应用开发日报,开源项目]
categories: [大模型应用开发日报]
description: 
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/5c13177bab2b0efb5d54a3345a42407d88509d8ba1c93d57408d64f85f231022.jpg
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/5c13177bab2b0efb5d54a3345a42407d88509d8ba1c93d57408d64f85f231022.jpg
---



## 开源项目推荐
- [vocode-core](https://github.com/vocodedev/vocode-core)
>Vocode是一个开源库,可以轻松构建基于语音的LLM应用程序。使用Vocode,您可以构建与LLM的实时流式对话,并将其部署到电话通话、Zoom会议等。您还可以构建个人助理或基于语音的国际象棋应用程序。Vocode提供了易于使用的抽象和集成,因此您需要的一切都在一个库中。
>
>**主要功能点**
>- 使用系统音频启动对话
>- 设置响应LLM代理的电话号码
>- 从您的电话号码发出电话,由LLM代理管理
>- 拨入Zoom通话
>- 在Langchain代理中使用外拨电话号码
>
>**技术栈**
>- 语音转录服务:AssemblyAI、Deepgram、Gladia、Google Cloud、Microsoft Azure、RevAI、Whisper、Whisper.cpp
>- 语言模型:OpenAI、Anthropic
>- 语音合成服务:Rime.ai、Microsoft Azure、Google Cloud、Play.ht、Eleven Labs、Cartesia、Coqui (OSS)、gTTS、StreamElements、Bark、AWS Polly

- [SenseVoice](https://github.com/FunAudioLLM/SenseVoice/blob/main/README_zh.md)
>SSenseVoice是一个具有多种语音理解能力的语音基础模型,包括自动语音识别(ASR)、语音语言识别(LID)、语音情感识别(SER)和音频事件检测(AED)。它在多语言语音识别、语音情感识别和音频事件检测方面表现出色,并且具有高效的推理性能。
>
>**主要功能点**
>- 支持50多种语言的高精度多语言语音识别
>- 具有出色的情感识别能力,在测试数据上超越了当前最佳的情感识别模型
>- 提供声音事件检测能力,支持检测各种常见的人机交互事件
>- SenseVoice-Small模型采用非自回归端到端架构,推理延迟极低,比Whisper-Large快15倍
>- 提供便捷的微调脚本和策略,用户可以根据业务场景轻松解决长尾样本问题
>- 提供服务部署流水线,支持多并发请求,客户端语言包括Python、C++、HTML、Java和C#等


## 技术介绍

## 扩展阅读
- [AI工程师指南：我是谁，从哪来，到哪去？｜对谈硅基流动创始人袁进辉与独立开发者idoubi](https://mp.weixin.qq.com/s/mUoeQv6lrSX-M0w8LNqH7w)
>本文是‘十字路口’播客的一期节目，邀请了硅基流动创始人袁进辉和独立开发者 idoubi，共同探讨 AI 工程师的职业现状、未来发展方向以及 AI 技术在实际应用中的挑战与机遇。
>
>文章强调 AI 工程师面临快速变化的行业环境和多样的职业路径选择，特别是 AI Native 应用的重要性。idoubi 分享了在 AI 应用开发中的高效辅助作用，并讨论了提示词工程和低代码开发的趋势。此外，文章还探讨了全栈工程师的需求以及 AI 时代下工程师角色的转变，最后强调了创业过程中的自我革新和个人成长。
>
>**主要内容**:
>1. AI 工程师的职业路径多样性 -- AI 工程师处于技术变革的前沿，面临快速变化的行业环境和多样的职业路径选择。
>2. AI Native 应用的重要性 -- 袁进辉和 idoubi 强调了 AI Native 应用的重要性，认为这是未来发展的主流方向。
>3. 提示词工程和低代码开发趋势 -- 提示词工程已成为开发 AI 应用的基础，而低代码开发趋势使得 AI 应用开发更高效和便捷。
>4. 全栈工程师的需求 -- 随着 AI 和云服务的发展，全栈工程师的需求增加，个人开发者可以利用外部资源快速构建产品。
>5. 创业和个人成长 -- 创业不仅是业务发展，更是一个自我革新和突破的过程，需要持续的成就感和动力。

- [李沐交大演讲全文：创业的动机要么来自欲望，要么来自恐惧](https://mp.weixin.qq.com/s/ceyTAwHlFyS3Wh78ZLefrQ)
>李沐在上海交大的演讲中深入探讨了 AI 技术的发展趋势、创业动机以及个人职业发展，强调了数据、算力和算法在 AI 领域的核心作用，并分享了创业和学术研究的个人见解。
>
>李沐在演讲中详细讨论了 AI 技术的多个方面，涵盖了大模型的算力需求、内存瓶颈、多模态技术的发展趋势以及 AI 在不同职业领域的应用现状。他通过生动的比喻将机器学习比作炼丹，指出数据、算力和算法是炼制高质量模型的核心要素。此外，他分享了创业一年半的经验，强调了强烈动机的重要性，以及如何通过自我反思和持续努力提升个人能力。在这个充满机遇与挑战的时代，他呼吁大家把握新技术带来的红利。
>
>**主要内容**:
>1. 大模型的算力、数据和算法是 AI 发展的关键要素 -- 数据是炼丹的材料，算力是火力和设备，算法是丹方。内存和带宽是当前模型尺寸的瓶颈，未来技术发展将集中在这些硬件的改进上。
>2. 预训练是一个工程问题，后训练才是技术问题 -- 高质量的数据和改进的算法能极大提升模型效果。垂直模型虽被认为是解决特定任务的方案，但实际上通用能力同样重要，没有真正的垂直模型。
>3. AI 在不同职业领域的应用现状和未来发展 -- AI 在文科白领工作中的应用已达到可接受水平，但在工科白领和蓝领工作中仍需进一步发展。自动驾驶是 AI 在蓝领工作中唯一表现出色的领域，但整体上 AI 与物理世界的互动仍需大量时间和技术突破。
>4. 强烈的动机要来自欲望或恐惧 -- 李沐强调，创业者的强烈动机通常源于深沉的欲望或恐惧，这种动机是推动成功的重要动力。


### 提示工程学习资料
[Prompt Engineering Guide](https://promptingguide.ai)
>一个开源的 Prompt Engineering 学习资源网站，循序渐进系统的讲解了提示工程的方方面面，并且包含多语言版，中文版我还贡献了几页内容的翻译。
>
>这个网站适合系统的快速浏览一遍有一个全局了解，时不时回头来翻一翻。

#### Anthropic 的 Prompt Engineering 资源
  - [Prompt Engineering 文档](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
>Anthropic 的文档网站做的相当不错，其中就有很重要的一部分是 Prompt Engineering 相关的，这部分主要是结合它自家的 Claude 模型来讲的，算是 Claude 的最佳实践：
>- 指令要清晰直接
>- 使用样例
>- 链式思考
>- 使用 XML 来结构化输入和输出
>- 给 Claude 设定角色
>- 其他
>
>上面的最佳实践虽然是针对 Claude，但基本上对绝大部分模型都适用，但也要要注意些差别，比如对样例 Claude 可以很多样例，效果很好，这是因为它上下文长度很长，并且遵循指令也做得很好，同样的用在其他模型上未必效果会好；还有 Claude 对于 XML 是专门微调过的，支持的相当好，但是对于其他模型，未必 XML 是最佳格式。
  - [Anthropic Prompt Library](https://docs.anthropic.com/en/prompt-library/library)
>它有一系列的常用 Prompt 库，通过学习这些 Prompt 示例，可以大概了解对于不同场景，怎么写 Prompt 是最好的。

  - [Anthropic courses](https://github.com/anthropics/courses)
>Anthropic 出的开源 Prompt 教程，其中包含四门课程：
>1. Anthropic API基础课程 - 教授使用Claude SDK的基本要点：获取API密钥、操作模型参数、编写多模态提示词、流式响应等。
>2. 提示词工程交互式教程 - 一步步详细指导关键提示技术。
>3. Google Vertex版本
>4. 现实世界中的提示工程课程 - 学习如何将提示技术应用于复杂的现实世界提示中。
>
>尤其是其中的现实世界中的提示工程课程很不错，首先回顾了其官方文档中的最佳实践，然后结合几个常见的应用案例，一步步从错误实践到普通实践到最佳实践，配合 jupyter notebook，让你可以看到每一种优化方案的执行结果。
>包含的几个案例都很有代表性：
>- 从医疗报告中提取结构化信息
>- 对客户呼叫电话生成摘要
>- 客服售后支持
  - [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook)
>这是偏向 Anthropic 开发者的代码示例，不仅仅是 Prompt Engineering，还有其他一些内容，比如 Embedding、微调等等

#### [DeepLearning](https://deeplearning.ai)
>这是吴恩达老师办的面向深度学习的课程，似乎都是免费的，上面的课程不仅有教学视频，还有一个可以运行代码的环境，可以按照课程写代码执行，其中有很多课程很适合 AI 初学者。
- [Generative AI for Everyone](https://deeplearning.ai/courses/generative-ai-for-everyone/)
    > 非常适合初学者全面了解生成式 AI 的课程
- [ChatGPT Prompt Engineering for Developers](https://deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/)
    >结合 ChatGPT 以及几个常见案例的 Prompt Engineering 入门教学视频
#### OpenAI 的 Prompt Engineering 学习资源
>OpenAI 也出了很多优质的 Prompt Engineering 学习资源。

- [Prompt engineering 指南](https://platform.openai.com/docs/guides/prompt-engineering)
    >它的 Prompt engineering 文档上面有各种 Prompt 使用的最佳实践，总结的六个策略非常有代表性：
    >1. 策略一：撰写清晰的指令
    >2. 策略二：提供参考文本
    >3. 策略三：把复杂的任务拆分成简单的子任务
    >4. 策略四：给模型更多时间“思考”
    >5. 策略五：运用外部工具
    >6. 策略六：系统地对变更进行测试

- [OpenAI 的 Prompt examples](https://platform.openai.com/docs/examples)
    >这里列了很多常用的 Prompt，比如翻译、做数学题、面试准备问题、解释代码等等，并且每一个 Prompt 示例，不仅有代码，还包含了如何使用代码调用
- [OpenAI Cookbook](https://cookbook.openai.com)
    >OpenAI 的 Cookbook 是学习调用 OpenAI 各种 API 的宝库，能找到很多常见案例的代码，里面不仅有详细的说明，并且有代码示例。
#### 其他
- [Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners/)
    >微软在出教程上也是很积极的，他们有一套《Generative AI for Beginners》很不错，而且一直在更新，现在都出到 V2 了.一共有 18 节课，自带中文版.
- [Prompt Engineering for Generative AI](https://developers.google.com/machine-learning/resources/prompt-eng)
    > Google 的 AI 教程也不少，有相当多的视频教程，除了上面的提示工程的，还有很多其他 AI 相关教程，你可以去它网站上找


- [IBM Technology](https://youtube.com/@IBMTechnology)
    >IBM 在 YouTube 上有个频道叫 IBM Technology，上面有很多高质量的 AI 教学视频，每一集都不长，看看很有收获。

- [Stanford CS25](https://youtube.com/watch?v=P127jhj-8-Y&list=PLoROMvodv4rNiJRchCzutFw5ItR_Z27CM)
    >CS25 是斯坦福的一门课《Transformers United》，讲 Transformer 的，到现在已经讲到第四版了，并且每一次都会邀请一些业界专业人士来讲课，比如上学期就有 OpenAI 的 Jason Wei 和 Hyung Won Chung、Hugging Face 的 Loubna Ben Allal 这些大神去客串讲课


- [Deep Learning by 3Blue1Brown](https://youtube.com/@3blue1brown)
    >3Blue1Brown 很多人都知道，他做的视频深入浅出，能将复杂的理论讲的相对容易听懂，他最近一直在连载 Deep Learning 相关的课程，已经讲到第 7 课了，都有高质量的中文字幕。


- [CS50](https://pll.harvard.edu/subject/artificial-intelligence)
    >哈佛大学的 CS50 课程很有名，都是计算机相关的课程，免费向大众开放，其中也包括 AI 相关的课程。
    >值得一提的是，他们引入了 AI 作为助教，以一只小黄鸭为形象，来源是程序员常用的小黄鸭调试法。


- [http://freeCodeCamp.org ](https://youtube.com/@freecodecamp)
    >这是一个收集了各种开发相关免费视频教程的油管频道，其中有不少就是 AI 相关的教学视频，质量不错。

- [LangChain ](https://youtube.com/@LangChain)
    >LangChain 的 YouTube 频道做的不错，上面经常会发一些高质量的教学视频，虽然都是围绕 LangChain，但是抛除 Langchain 的部分，很多都是通用的，尤其是 RAG 相关的。



- [Andrej Karpathy](https://youtube.com/@AndrejKarpathy)
    >Andrej Karpathy 是前 OpenAI 创始人之一，前特斯拉自动驾驶的负责人，他的油管频道上有很多专业的 AI 相关教学视频，质量很高，比如教你从头写一个 GPT 之类，听说在有的大学里面他的视频都属于辅助教学的材料。