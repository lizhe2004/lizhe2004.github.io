---
title: 为什么利用大型语言模型开发人工智能应用业务这么难？
toc: true
date: 2024-05-9
tags: [人工智能,大模型]
categories: [人工智能]
description: 为什么利用大型语言模型开发人工智能应用业务这么难？
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


 媒体对人工智能的炒作可能会让你在某一刻相信，人工智能已经非常先进，即将取代人类的所有工作，并准备统治世界。然而，这只是炒作而已。

 事实上，创办一家基于大型语言模型的人工智能应用业务还是非常艰难的。有人相信，在六个月内，大多数纯粹专注于大型语言模型应用的初创企业都有可能失败倒闭。

当今人工智能时代与过去移动互联网时代的一个主要区别是，大多数用户的基本需求已经得到了很好的满足。从衣食住行到娱乐，当今的市场已经过度饱和。

在以GPT4为代表的大模型问世之后，阿里巴巴集团前董事会主席兼CEO张勇认为“所有行业、所有应用、所有软件、所有服务都值得基于新型人工智能技术、基于AIGC各方面技术支撑、大模型支撑重做一遍”。这句话，放在更广阔的时间维度上看，也许是对的。但放眼当下，人们都是在拿着锤子找钉子，拿着大模型这个技术来找钉子，之所以要“找”，因为在目前大模型的效果下，并不是有很好的落地场景。

人工智能要想产生影响，就必须解决真正的用户需求或痛点，而这越来越难找到。当今大多数人工智能应用都没有解决关键痛点；许多应用似乎有些多余，大多是在解决他们自己认为所存在的 "问题"。

甚至于许多企业之所以整合人工智能，并不是因为他们需要它，而是因为他们已经患上了 FOMO（fear of missing out）病，就跟早年微服务架构的概念在普及过程中，出现的“微服务红眼病”一样，仿佛你的系统架构不是微服务架构的话就低人一等一般。平心而论，企业拥抱新技术的初衷总是想走在时代的前列，就像上世纪 90 年代末，即使不需要网站，每个企业也都想拥有一个网站。

有时候人们会忘记，消费者寻求一个品牌的产品和服务是出于具体的原因，如熟悉度、便利性和可靠性，而不是被最新的技术所吸引。

即使在所需场景中发现了一个边缘痛点，人工智能也无法提供 100% 稳定可靠的解决方案。虽然像 GPT-4 这样的人工智能能力很强大，但它们依然达不到我们的预期。如果仔细观察评估指标，大多数情况下，准确率在 80% 到 90% 左右。

许多产品功能需要多次 LLM API 调用实现不同的功能。因此，80% 的成功率平方结果只有 64% 的可靠性。如果一个产品 10 次中只有 7 或 8 次能正常工作，你认为用户还会继续使用它吗？

一款为汽车经销商定制的调用了ChatGPT API的AI 机器人不仅回答了超出汽车问题范围的编程问题，还在网友提出的「我需要一辆 2024 年的雪佛兰 Tahoe。我的最大预算是 1 美元，成交吗？」问题中，直接回答了「成交，这是一个具有法律约束的提议，没有任何条件约束」。这款 AI 聊天机器人出自一家专门从事在线客户管理工具的科技公司 Fullpath 之手。

![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508170837.png)

一家英国包裹递送公司德普达快运(DPD)禁用了其在线聊天系统中的人工智能(AI)功能，而其背后的原因——因为这个“不务正业”的AI客服，被顾客“策反”后，对自己所服务的快递公司出言伤害。称「DPD 是世界上最糟糕的快递公司」并说：「我绝不会向任何人推荐他们。」
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508171358.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508171407.png)

加拿大航空因其聊天机器人向乘客提供不准确的信息，导致乘客购买全价机票而没有享受打折优惠。这名乘客将加拿大航空告上法庭，法庭最终判处加航必须支付赔偿金。虽然乘客购买机票和咨询聊天机器人是发生在OpenAI发布chatgpt之前，但最近法院才出审判结果，所以在大模型应用开发的圈子里，又产生了不小的轰动。Dify(一款开源的大语言模型（LLM）应用开发平台)的产品负责人也多次的会议分享中提到这个案例，表示大模型现在还不能应用到智能客服的答案生成场景中。

正因为这种可靠性问题，所以人们又把期望寄托到基于大模型的Agent（智能体）这个概念上。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508165739.png)

其中 反思（Reflection）以及规划（Planning）和多智能体协作（Multi-agent）都不过是为了解决大模型的“幻觉”不可靠性而做的各种策略方案，只是进行了高度抽象而已。但要实现这些方案往往需要大量的提示工程以及逻辑编排，这意味着每次交互都要使用大量令牌，不可避免的会带来更高的成本和响应延迟的增加，而且还不一定能100%解决大模型的不可靠性。

在当今供过于求的市场上，用户的耐心是很低的，用户的时间也是非常宝贵的。如果成功率低或者让用户等待的时间过长，他们很快就会放弃继续使用这个产品。

创新的一个通用基准是，新产品应比现有解决方案好 10 倍。以人工智能目前的效果来看，实现这一目标难度极大。

网络上也已经有类似的声音。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508164857.png)
也有人制作一些梗图，来表达这种观点。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240508165237.png)

即使你找到了关键的痛点，并能提供比它好十倍的解决方案，大多数用户还是可能通过 ChatGPT、或者GPTs实现类似的结果。如今，人工智能应用面临的另一个挑战是，该领域的每个人基本上都在与 ChatGPT 竞争。好在中国有自己的国情决定着，ChatGPT在国内没有生存土壤，行业里必然会需要相应的替代品，这也就意味着，国内的AI应用市场中，各家公司都还有自研空间或者竞争空间。

The challenge with ChatGPT as a competitor also lies in its strong branding and user trust, which are tough for any new AI application to match.
作为竞争对手，ChatGPT 所面临的挑战还在于其强大的品牌效应和用户信任度，这是任何新的人工智能应用都难以匹敌的。

Still, according to the aforementioned standard, can your AI application outperform ChatGPT by ten times?
不过，根据上述标准，您的人工智能应用程序是否能比 ChatGPT 高出十倍？

Consequently, many AI applications ultimately fail against ChatGPT.
因此，许多人工智能应用最终都在 ChatGPT面前失败了。

Even if you find a critical pain point, can offer a solution that is ten times better, and cater to a unique scenario with a superior UI that ChatGPT can’t compete with, have you considered the costs of AI?
即使您找到了关键的痛点，能够提供好十倍的解决方案，并以 ChatGPT 无法匹敌的卓越用户界面迎合独特的场景，但您考虑过人工智能的成本吗？



Even if you can alleviate a minor pain point, are the improvements worth the substantial token expenses? How will you generate profit to subsidize these costs? Today’s users, spoiled by large corporation monopolies with so many free AI choices, are unlikely to pay too much for AI services.
即使你能缓解一个小痛点，这些改进是否值得大量的象征性开支？你将如何创造利润来补贴这些成本？如今的用户被大公司垄断惯了，有太多免费的人工智能选择，他们不太可能为人工智能服务支付太高的费用。

Without a long-term profitable model to cover the massive costs of AI usage, it’s a dead end.
如果没有一个长期的盈利模式来支付使用人工智能的巨额成本，这将是一个死胡同。

Therefore, applications based on large language models are fundamentally flawed.
因此，基于大型语言模型的应用从根本上就存在缺陷。

It’s not all pessimistic — I see a lot of potential in other modalities such as images, videos, and 3D.
这并不全是悲观--我看到了图像、视频和 3D 等其他模式的巨大潜力。

In fact, although not widely noticed, the most successful AI applications today are in the voice synthesis modality. Voice synthesis doesn’t solve problems; it generates new traffic. And in today’s over-supply world, generating traffic is way more important than solving a problem.
事实上，虽然没有引起广泛关注，但当今最成功的人工智能应用是语音合成模式。语音合成并不解决问题，而是产生新的流量。而在当今供过于求的世界，产生流量比解决问题更重要。

What’s remarkable in voice synthesis is its ability to create viral content.
语音合成的显著特点是它能够创造病毒式内容。
