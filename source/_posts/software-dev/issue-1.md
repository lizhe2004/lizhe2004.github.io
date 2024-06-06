---
topic: software-dev # 这是项目id，对应 /data/wiki/hexo-stellar.yml
title: 程序员日报-2024-06-06
toc: true
menu_id: topic
date: 2024-06-06
tags: [程序员日报,职业发展,VUE-Flow,开源项目]
categories: [程序员日报]
description: 一些markdown转微信公众号工具以及icon网站合集，推荐了开源工具：流程图编辑工具VUE-Flow、相册网站PicImpact、问卷系统xiaoju-survey、网盘搜索系统aipan-netdisk-search，最后分享了中国键盘历史以及设计师职业发展建议的文章。
banner: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605195926.png
cover: https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605195926.png
---
## 编程资料

## 高效工具
**Markdown转微信公众号工具**
- [https://md.qikqiak.com/](https://md.qikqiak.com/)
  - [开源 https://github.com/cnych/markdown-weixin](https://github.com/cnych/markdown-weixin)
- [https://wangchujiang.com/wxmp/#/?theme=default](https://wangchujiang.com/wxmp/#/?theme=default)
  - [开源 https://github.com/jaywcjlove/wxmp](https://github.com/jaywcjlove/wxmp)
- [https://prod.zkqiang.cn/wxeditor/index.html](https://prod.zkqiang.cn/wxeditor/index.html)
  - [开源 https://github.com/zkqiang/wechat-mdeditor](https://github.com/zkqiang/wechat-mdeditor)
- [https://wechat.bmpi.dev/](https://wechat.bmpi.dev/)
- [https://md.mazhuang.org/](https://md.mazhuang.org/)
  - [开源 https://github.com/mzlogin/online-markdown](https://github.com/mzlogin/online-markdown)
- [https://markdown.com.cn/editor/](https://markdown.com.cn/editor/)
- [https://doocs.github.io/md/](https://doocs.github.io/md/)
  - [开源 https://github.com/doocs/md](https://github.com/doocs/md)
- [https://ruanyf.github.io/wechat-format/](https://ruanyf.github.io/wechat-format/)
  - [开源 https://github.com/lyricat/wechat-format](https://github.com/lyricat/wechat-format)
- [https://quail.ink/tools/markdown-to-wx/](https://quail.ink/tools/markdown-to-wx/)

**icon网站合集**
- [fontawesome：https://fontawesome.com/icons](https://fontawesome.com/icons)
- [react-icons：https://react-icons.github.io/react-icons/](https://react-icons.github.io/react-icons/)
- [iconify：https://icon-sets.iconify.design](https://icon-sets.iconify.design)
- [lucide：https://lucide.dev](https://lucide.dev)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606115442.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606115502.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606115516.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606115534.png)

## 职业发展
[如何成为一名高级设计师【英文版】](https://bootcamp.uxdesign.cc/how-to-become-a-senior-designer-from-an-ex-google-meta-designer-6092866bd2aa)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605195926.png)
- 成长是自我发起的：不应该等待机会，而是要主动创造机会。
- 从执行者转变为拥有者：作为资深设计师，需要对团队整体方向和目标负责，而不仅仅是执行任务。
- 勇于发声：即使不完全确定，也应该表达自己的意见，因为在设计和产品开发中没有绝对正确或错误的答案。
- 面对挑战时寻求理解：在与他人的意见不合时，应该寻求理解，而不是试图赢得争论。
- 克服恐惧和疑虑：恐惧和疑虑在追求新挑战时是不可避免的，但不应让它们阻止个人成长。

## 开源项目
[VUE-Flow](https://github.com/bcakmakoglu/vue-flow)
基于Vue3的高度可定制的流程图组件。具有无缝缩放和平移、迷你地图等附加组件以及与状态、动画效果和图形交互等功能。
效果图：
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605195028.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240605195125.png)

[PicImpact](https://github.com/besscroft/PicImpact)
>一个摄影师专用的摄影作品展示网站，基于 Next.js 开发。采用Postgre 数据库
>功能特性
>- 瀑布流相册展示图片，支持常见的格式。
>- 点击图片查看原图，浏览图片信息和 EXIF 信息。
>- 响应式设计，在 PC 和移动端都有不错的体验，支持暗黑模式。
>- 图片存储兼容 S3 API、Cloudflare R2、AList API。
>- 图片支持绑定标签，并且可通过标签进行交互，筛选标签下所有图片。
>- 上传图片时会生成 0.3 倍率的压缩图片，以提供加载优化。
>- 图片版权信息展示和维护功能，支持外链跳转。
>- 后台有图片数据统计、图片上传、图片维护、相册管理、系统设置和存储配置功能。
>- 基于 SSR 的混合渲染，采用状态机制，提供良好的使用体验。
>- 基于 prisma 的自动初始化数据库和数据迁移，简化部署流程。
>- 支持 Vercel 部署、Node.js 部署、Docker 等容器化部署，当然 k8s 也支持
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606133228.png)

[xiaoju-survey](https://github.com/didi/xiaoju-survey)
> XIAOJUSURVEY是一套轻量、安全的问卷系统基座，提供面向个人和企业的一站式产品级解决方案，快速满足各类线上调研场景。
>内部系统已沉淀 40+种题型，累积精选模板 100+，适用于市场调研、客户满意度调研、在线考试、投票、报道、测评等众多场景。数据能力上，经过上亿量级打磨，沉淀了分题统计、交叉分析、多渠道分析等在线报表能力，快速满足专业化分析。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606132858.png)

[ibelick](https://bg.ibelick.com/)
>[源码](https://github.com/ibelick/background-snippets)
>如果觉得网站背景纯色太单调，渐变又有点太花哨，可以来这找找灵感.网站收集了一系列可以直接使用的网页背景色（包括渐变效果等）以及代码片段可以用于原生CSS、Tailwind CSS等。
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606133540.png)

[2024年前端工程师手册(英文版)](https://github.com/FrontendMasters/front-end-handbook-2024)
- [在线阅读](https://frontendmasters.com/guides/front-end-handbook/2024/)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606133302.png)

[aipan-netdisk-search](https://github.com/unilei/aipan-netdisk-search)
>一个基于vue、nuxt.js的网盘搜索项目,目前代码仓库已经存档，只读。

[onur.dev](https://github.com/suyalcinkaya/onur.dev)
>onur.dev 是 Onur Şuyalçınkaya 的开源博客模板，基于 shadcn/ui 框架，拥有精美的视觉设计和流畅的用户体验 🎨。通过 Contentful 进行内容管理，让写作和发布变得简单高效 ✍️。onur.dev 也支持移动端展示📱，确保您的内容在任何终端上都能得到完美的呈现。无论是用作个人博客，还是作为专业导航站点都是很好的选择。

[public-apis-cn](https://github.com/llf007/public-apis-cn)
>将public-apis项目翻译为中文版，并收集添加国内常用API,涉及天气、国内物流、AI模型、地理定位、节日等。

[答案之书](https://github.com/unilei/answer-book)
>默念你的问题，点击下面的按钮，就可以拿走一个简单的答案和暗示
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606134158.png)

## 扩展阅读
[中国键盘被遗忘的历史](https://spectrum.ieee.org/chinese-keyboard)
>今天大家用 QWERTY 键盘输入中文，以前曾出现过多种专用中文键盘
美国汉学家墨磊寧 (Thomas S. Mullaney)出版的《中文计算机：信息时代的全球史》，揭示了 20 世纪中文输入键盘、中文输入方法被遗忘的历史
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606114824.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606114927.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606114949.png)
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240606115004.png)