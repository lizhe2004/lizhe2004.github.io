---
topic: llm-app # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 大模型应用开发日报-2024-06-06
menu_id: topic
toc: true
date: 2024-06-06
tags: [大模型应用开发日报,开源项目,RAG,uptrain,pipecat,godaddy,linkedin]
categories: [大模型应用开发日报]
description: 介绍了大模型开源工具julep、instructor、Qmedia、uptrain、pipecat、RAGApp等，分享了godaddy、linkedin等公司大模型应用开发的经验，提供了一个提示词注入攻击的介绍视频，最后介绍了传统程序员学习大模型的切入点、路径和侧重点。
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/00bfd9a1baf8fa4d8d16006437f427a7827f6b925a40c93202187a6bead01d9a.jpg
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/00bfd9a1baf8fa4d8d16006437f427a7827f6b925a40c93202187a6bead01d9a.jpg
---
## 开源项目推荐

[**julep** 链接](https://github.com/julep-ai/julep)
> 1. 提供构建 AI Agents 框架级的能力，内建 Memory、Knowledge、Tools🥳
>2. 基于开源的 AI 图向量数据库 CozoDB 构建 Stateful AI 应用 
>3. 基于@composiohq, 支持 90+ Tools

[instructor](https://github.com/jxnl/instructor)
>Instructor 是一个 Python 库，可以轻松处理大型语言模型（LLMs）的结构化输出。它建立在 Pydantic 的基础之上，提供了一个简单、透明和用户友好的 API 来管理验证、重试和流式响应。
```python
import instructor
from pydantic import BaseModel
from openai import OpenAI
# Define your desired output structure
class UserInfo(BaseModel):
    name: str
    age: int

# Patch the OpenAI client
client = instructor.from_openai(OpenAI())

# Extract structured data from natural language
user_info = client.chat.completions.create(
    model="gpt-3.5-turbo",
    response_model=UserInfo,
    messages=[{"role": "user", "content": "John Doe is 30 years old."}],
)

print(user_info.name)
#> John Doe
print(user_info.age)
#> 30
```
[Qmedia](https://github.com/QmiAI/Qmedia)
>专为内容创作者设计的开源人工智能内容搜索引擎。支持文本、图片、短视频的提取。允许完全本地部署（Web 应用程序、RAG 服务器、LLM 服务器）。支持多模态RAG内容问答。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606134915.png)

[awesome-ai-agents](https://github.com/e2b-dev/awesome-ai-agents)
>收集了业内一系列的AI Agents，分为开源和闭源两个类型。
类别方向会分为：Coding、Research、Data Analysis、Productivity、Build my own、Multi-agent、General purpose 方向。
![](https://cdn.jsdelivr.net/gh/e2b-dev/awesome-ai-agents@main/assets/landscape-latest.png)

[uptrain](https://github.com/uptrain-ai/uptrain)
>一个用于评估和改进生成式 AI 应用程序的开源统一平台。我们为 20 多个预配置检查（涵盖语言、代码、嵌入用例）提供评分，对失败案例进行根本原因分析，并提供有关如何解决这些问题的见解。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606135955.png)

[pipecat](https://github.com/pipecat-ai/pipecat)
>pipecat 是用于构建语音（和多模式）对话代理的框架。比如私人教练、会议助理、儿童讲故事玩具、客户支持机器人
集成了各个 ASR/LLM/TTS AI 能力： anthropic, azure, deepgram, google, fal, moondream, openai, playht, silero, whisper
支持了实时的传输：websocket 以及 WebRTC(通过 trydaily的 RTC 服务)。
支持Voice Activity Detection 语音活动检测。

[小胰宝](https://github.com/PancrePal-xiaoyibao/PancrePal-xiaoyibao)
>小胰宝 - 面向胰腺癌肿瘤患者的智能RAG平台(公益项目)，一名癌末 IT 老兵留給世界的赠礼。 
旨在帮助每年数十万新增确诊病人以及幸存病人，克服专业医学和治疗的医患信息差。使用小胰宝，可7x24小时，帮助病患高效率，准确理解病情状态，治疗术语，规范治疗指南，以及综合治疗的复杂信息，克服慌乱情绪，选择科学和有效治疗路线，并最终获得更长的治疗收益，也即生命窗口。

[RAGApp](https://github.com/ragapp/ragapp)
>基于llamaindex构建的Agentic RAG应用，支持docker部署，提供了管理后台、聊天页面以及API接口。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606131639.png)

[phidata](https://github.com/phidatahq/phidata)
>Phidata 是一个用于构建自主助理（又称 "代理"）的框架，它拥有长期记忆、上下文知识以及使用函数调用采取行动的能力。
[awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps)
> 一系列大模型应用代码示例，比如
> - 生成式人工智能网络搜索助手
>  - 人工智能投资机器人智能体
> - AI 驱动的记者机器人智能体
> - 与 YouTube 视频聊天

```python
#可以搜索网络的助手
from phi.assistant import Assistant
from phi.tools.duckduckgo import DuckDuckGo

assistant = Assistant(tools=[DuckDuckGo()], show_tool_calls=True)
assistant.print_response("Whats happening in France?", markdown=True)
```
[litgpt](https://github.com/Lightning-AI/litgpt)
>在您自己的数据上预训练、微调、部署 20 多个 LLM（Llama 3，Mistral、Phi等）。使用最先进的技术:flash attention, FSDP, 4-bit, LoRA等
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606135036.png)

[RAG Book](https://github.com/mallahyari/rag-ebook)
>《检索增强生成 (RAG) 系统的实用方法》一书的源文本
> [在线阅读](https://angelinamagr.gumroad.com/l/practical-approach-to-RAG-systems)


[ChatTTS_colab](https://github.com/6drf21e/ChatTTS_colab/)
>带音色种子管理的 ChatTTS 项目，可以部署在Colab，亦可离线下载到本地部署。通过网页访问ChatTTS服务。支持音色抽卡、长音频生成和分角色朗读。简单易用，无需复杂安装。

[ChatTTS-ui](https://github.com/jianchang512/ChatTTS-ui)
>一个简单的本地网页界面，直接在网页使用 ChatTTS 将文字合成为语音，支持中英文、数字混杂，并提供API接口。

[openui](https://github.com/wandb/openui)
>利用大模型生成web网页，自己文本描述 UI，然后查看它的实时渲染。 用户可以要求更改并将 HTML 转换为 React、Svelte、Web Components 等。它类似于 v0，但是开源的，而且没有那么精美
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/demo.gif)


## 技术介绍
[什么是提示词注入攻击？（双语字幕）](https://www.youtube.com/watch?v=jrHRe9lSqqA&ab_channel=IBMTechnology)

> 这部视频把什么是提示词注入攻击以及如何预防从理论方面讲的比较清楚了，不过没有什么实操的技巧让你可以学以致用的😅
但还是值得学习一下，帮助你更好的理解大语言模型为什么会被提示词注入攻击。

## 开发经验

[使用大语言模型 (LLMs) 构建产品一年后的经验总结 (第一部分) [译]](https://baoyu.io/translations/llm/what-we-learned-from-a-year-of-building-with-llms-part-1)
> 详细分享了使用大语言模型（LLMs）构建产品一年来的经验和最佳实践，涵盖提示设计、信息检索、工作流调整和评估监控等方面。
> - **提示设计至关重要**：提示设计是构建 LLMs 产品的关键步骤，需要平衡正确的技术使用和工程工作量。提示词应该简洁而专注，避免过度复杂化。
> - **输入输出结构化**：结构化的输入和输出可以帮助模型更好地理解和处理信息，提高与下游系统的集成效率。
> - **检索增强生成（RAG）的作用**：RAG 是一种有效的方法，可以提供知识作为提示的一部分，提高 LLMs 在特定任务上的表现。
> - **RAG 优于微调**：文章中提到的研究表明，RAG 在提供新知识和改进输出方面优于微调，并且具有实际优势，如更容易更新检索索引。
> - **长上下文模型不会取代 RAG**：尽管长上下文模型提供了更大的上下文窗口，但 RAG 仍然有其独特的应用场景和优势。
> - **工作流调整和优化**：通过多轮的 “流程” 设计和确定性工作流程，可以显著提升 LLMs 的效果和可靠性。
> - **评估和监控的重要性**：严格而周密的评估和监控对于确保 LLMs 产品的质量至关重要。文章提供了多种评估策略，包括基于断言的单元测试和 LLM-as-Judge。
> - **保护措施的必要性**：应对 LLMs 在不应该生成内容时的输出问题，以及处理事实不一致问题，是构建可靠 LLMs 产品的关键。
> - **幻觉问题难以解决**：LLMs 生成事实不一致内容的问题是顽固的，需要通过提示工程和事实不一致防护措施相结合来解决。
 
[在 GoDaddy 实施模型开发的10个经验教训](https://www.godaddy.com/resources/news/llm-from-the-trenches-10-lessons-learned-operationalizing-models-at-godaddy#h-1-sometimes-one-prompt-isn-t-enough)

> - **有时候一个提示不足以应对复杂的对话流程** GoDaddy 发现在对话中使用任务导向型的提示比使用单一的超级提示更高效。
> - **对于结构化输出需要谨慎** 虽然 AI 机器人的纯文本回复适合聊天场景，但对于需要 AI 分析的系统来说，结构化的回复更为有效。
> - **对于结构化输出需要谨慎** 虽然 AI 机器人的纯文本回复适合聊天场景，但对于需要 AI 分析的系统来说，结构化的回复更为有效。
> - **提示不能跨模型移植**不同的模型甚至相同模型的不同版本在性能上会有显著差异，需要针对性地调整和测试提示。
> - **对于结构化输出需要谨慎** 虽然 AI 机器人的纯文本回复适合聊天场景，但对于需要 AI 分析的系统来说，结构化的回复更为有效。
> - **AI 的 “护栏” 至关重要** 为了防止 AI 输出的不确定性，GoDaddy 实施了多种控制措施，包括检查个人信息和不当内容，以及在特定情况下转接到人工服务。
> - **模型可能会慢且不可靠** GoDaddy 经历了模型提供商的完成失败，并且发现新一代的模型响应时间更长。
> - **内存管理很困难** 管理 LLMs 的上下文信息是一个巨大挑战，GoDaddy 探索了多种策略来优化这一点。
> - **自适应模型选择是未来的趋势** GoDaddy 认为根据不同的场景和需求动态选择模型可以提高可靠性和降低成本。
> - **有效使用 RAG（检索增强的生成）** RAG 可以帮助模型提供超出其参数化上下文的信息，但需要精心设计。
> - **为 RAG 调整数据。** GoDaddy 正在将其数据集转换为更适合模型使用的格式，以提高效率和性能。
> - **测试至关重要。** GoDaddy 强调测试 LLMs 集成的重要性，并建议建立报告系统以便 QA 团队进行审查。

[linkedin构建生成式人工智能产品的思考](https://www.linkedin.com/blog/engineering/generative-ai/musings-on-building-a-generative-ai-product)
>使用小模型用于将用户问题进行路由，决定查询是否在范围内，然后转发给不同AI agent 来回答。使用大模型用在最后生成回答
 有负责整体体验、评估、基础设施、UI 框架的开发团队，也有垂直负责不同Agent 场景的开发团队
 评估答案的品质比想像中更困难，目前先在内部建立了人工标注流程来获得品质指标(一天500则对话纪录)，之后想要建立自动化评估机制
  选择用YAML 来串接工具，因为比JSON 消耗更少tokens
但LLM 仍有10% 会输出错误的YAML，虽然retry 也可以，但是在分析LLM 常见错误后，改进了prompt 并透过程式检测并修补，就可以将错误率降低到0.01% 而不需要retry 
第一个月就可以达成理想目标80%的基本体验，接着四个月提升到95% 完整体验。但想要继续提升改进1% 的速度就很慢了
CoT 虽可以有效提升品质和减少幻觉，但这些推理用的输出tokens 用户不会看到(因为会移除不给用户看)，因此用户会觉得有latency ，而且也影响系统throughput。这是需要权衡的。 
端到端的Streaming 串流改进用户体验，包括串接外部工具也是逐步解析的，不需要等待LLM 完整输出，只要拿到其中一个工具参数就发出API调用。



## 其他
[大模型使用的合成器效应](https://webcache.googleusercontent.com/search?q=cache:https://medium.com/@mikeyd/the-synthesizer-effect-66a4e70a5289)
> - 电子音乐合成器是一种能够模拟和生成各种乐器声音的设备，它可以创造出与真实乐器比如钢琴、萨克斯、长笛等普通用户难以区分的音频效果。但是对于相应乐器的专业演奏人士而言，还是很容易区分出合成器产生的声音与真实乐器产生的声音之间的区别，而且认为两者差距很大。
> - 作者由此引申到大模型领域，作为程序员的作者很容易发现Github Copilot 这样的代码生成器生成的代码中的错误或问题，乃至于觉得是垃圾。但对于刚入门的学生或者产品经理、设计师等人员看到 Copilot 的输出时，看到的完全不是一回事。
> - 这也就是作者所说的“合成器效应”： 如果你知道自己在做什么，机器就骗不了你。如果你不知道，它就很可能骗过你。
> - 合成器效应让很多人对 LLMs 抱有疯狂膨胀的期望，不管这些期望是炒作出来的还是恐慌出来的。
>   - 首席执行官们认为 LLM 可以取代工程师。
>   - 工程师认为 LLM 可以取代销售人员。
>   - 销售人员认为 LLM 可以取代 CEO。
>   - 艺术家认为 LLM 可以取代其他人，
>   - 而其他人则认为 LLM 可以取代艺术家。

[GPT究竟是为地球上的什么人设计的 ](https://webcache.googleusercontent.com/search?q=cache:https%3A%2F%2Fai.gopubby.com%2Funited-uncoloured-gpts-for-which-humans-on-earth-are-llms-really-designed-3f353b0aced4)

>尽管 OpenAI 宣称致力于多样性、平等和包容性，但哈佛大学的研究团队通过全球性调查如世界价值观调查（WVS）和心理测量，发现 GPT-4 的回应与 WEIRD(Western西方、Educated教育型、Industrialized工业化、Rich富裕和Democratic民主) 国家的人类回应高度一致，而与非 WEIRD 国家的显著不同。这种偏见不仅体现在文化价值观和社会态度上，还影响了 LLMs 在心理学和社会学研究中的应用，如在多元文化交流和心理健康服务中的使用。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605202349.png)
通过这张图可以看出一个有趣的内容，中国不在任何一个分类里，很是独特，这可能也是我们文化与众不同的地方吧。

[传统程序员学习大模型的切入点、路径和侧重点](https://www.zhihu.com/question/629930332/answer/3493855000)
>正如一块草莓蛋糕，**算法工程师**可能从“**蛋糕胚**”这一层开始深入研究，理解其配方和做法，再逐步向上探索更高层次的奶油（应用）层；而**程序员**，应该先研究“**这块蛋糕该怎么吃**”，然后随着吃蛋糕的需要，自然而然地切下去，深入探索奶油层下面藏着的“蛋糕胚”。
因此对程序员来说，一上来就钻研算法，站的层太低了；钻研prompt，又太片面了。**程序员的切入点，应该在AI应用层**，即“蛋糕的吃法”上。
钻研大模型，对程序员来说比较舒适的路径是：
**提示词工程**->**调用api**->**AI应用开发框架**->**RAG技术**->**Agent**->**模型微调相关**->**模型产品部署和交付**

[SiliconCloud](https://siliconflow.cn/zh-cn/siliconcloud)
>这里有DeepSeek V2、Mistral、LLaMA 3、Qwen、SDXL、InstantID在内的多种开源大语言模型、图片生成模型，支持用户自由切换符合不同应用场景的模型。
目前每人注册就送3亿token
