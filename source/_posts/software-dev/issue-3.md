---
topic: software-dev # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 程序员日报-2024-08-23
toc: true
menu_id: topic
date: 2024-08-23
tags: [程序员日报]
categories: [程序员日报]
description: 
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/0f7bcefd4576c6036e2dcf2931f46fb8b365495ca8e10623890956e4e0759211.jpg
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/0f7bcefd4576c6036e2dcf2931f46fb8b365495ca8e10623890956e4e0759211.jpg
---
## 编程资料

[重试模式对于系统的弹性至关重要，但必须正确执行](https://x.com/RaulJuncoV/status/1824795622131568966)
>重试模式时需要记住的四个要点，以确保其正确实施：
>- 合理设置重试次数：建议最多重试三次，以避免因暂时性问题未能解决或因过多重试导致系统负载过大和持续问题识别延迟。
>- 实施指数退避策略(Exponential Backoff)：在每次失败的尝试后增加重试间隔时间，这有助于避免系统负载过大，并给予系统恢复的时间，防止所有失败请求同时重新打击系统。
>- 识别可重试的错误：只对瞬态错误进行重试，例如 408 请求超时和 5XX 服务器端错误，而不是不可恢复的错误，如 400 错误请求和 403 禁止错误。
>- 与断路器模式结合使用：重试模式与断路器机制相结合，可以防止对失败服务的重复调用。当达到一定失败次数后，断路器会打开，暂时阻止进一步的请求，从而给予服务恢复的时间。

## 高效工具
[cursor-AI加持的代码编辑器](https://www.cursor.com/)


[下载狗](https://www.xiazaitool.com/)
>下载狗 - 免费无水印视频下载器   支持全网100+主流网站
## 开源项目 

[spring-reading](https://github.com/xuchengsheng/spring-reading)
> 深入Spring，从源码开始！
> 探索Java最受欢迎的框架，理解它的内部机制，带大家从入门到精通。

[阿里巴巴低代码引擎](https://github.com/alibaba/lowcode-engine)
>- 🌈 提炼自企业级低代码平台的面向扩展设计的内核引擎，奉行最小内核，最强生态的设计理念
>- 📦 开箱即用的高质量生态元素，包括 物料体系、设置器、插件 等
>- ⚙️ 完善的工具链，支持 物料体系、设置器、插件 等生态元素的全链路研发周期
>- 🔌 强大的扩展能力，已支撑 100+ 个各种类型低代码平台
>- 🛡 使用 TypeScript 开发，提供完整的类型定义文件

[海棠诗社](https://github.com/javayhu/haitang)
>- 🎯 海棠诗社按诗集、朝代、诗人、诗词等方式检索，内容丰富，信息齐全
>- 📝 海棠诗社按选集、主题、节日、节气、词牌、时令、地理等方式精选分类
>- 🔍 海棠诗社全站响应式布局，兼容移动端，支持暗黑模式，响应速度快
>![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240823172032.png)


[favicon-downloader](https://github.com/seadfeng/favicon-downloader)
>FaviconExtractor 是一款功能强大的免费在线工具，可让您立即从任何网站检查和下载网站图标。支持从 16x16 到 512x512 的多种尺寸，可确保获得满足项目需求的完美图标。可以部署到CloudFlare上。并且提供了获取图标的API。
需要说明的是，该应用的界面被其他人发现抄袭了[https://www.redirectcheck.org/](https://www.redirectcheck.org/)

[pic-smaller](https://github.com/joye61/pic-smaller)
> 一个超级易于使用的在线图像压缩工具。它直观、移动友好,并支持压缩配置。同时,由于纯本地压缩没有任何服务器端逻辑,它是完全安全的。
> [Demo](https://picsmaller.com/)

[cursor.directory](https://github.com/pontusab/cursor.directory)
>cursor.directory 是一个开源项目,旨在帮助开发者找到最适合自己框架和语言的cursor(一款AI加持的开发IDE)编码规则。该项目提供了一个简单易用的界面,让开发者可以轻松地提交新的cursor规则。
在项目的根目录中复制并添加 .cursorrules 文件。
.cursorrules 文件中的说明将包含针对cursor chat和 Ctrl/⌘ K 等功能的说明。

[continue](https://github.com/continuedev/continue)
>Continue 是一个领先的开源 AI 代码助手。您可以连接任何模型和任何上下文,在 VS Code 和 JetBrains 中构建自定义代码自动完成和聊天体验。
主要功能点
>- 轻松理解代码段
>- 使用 tab 自动完成代码建议
>- 在您正在编码的地方重构函数
>- 询问有关代码库的问题
>- 快速使用文档作为上下文


## 扩展阅读
### 企业技术博客推荐
1 [Google Research](https://research.google/blog/)
2 [Meta Engineering](https://facebook.com/Engineering)
3 [AWS Blog](https://aws.amazon.com/blogs/aws/)
4 [Microsoft Engineering](https://learn.microsoft.com/en-us/devops/)
5 [Netflix Tech Blog](https://netflixtechblog.com)
6 [Figma Engineering](https://figma.com/blog/engineering/)
7 [Reddit Engineering](https://redditinc.com/blog)
8 [Spotify Engineering](https://engineering.atspotify.com)
9 [Slack Engineering](https://slack.engineering)
10 [Uber Engineering](https://uber.com/en-DE/blog/engineering/)