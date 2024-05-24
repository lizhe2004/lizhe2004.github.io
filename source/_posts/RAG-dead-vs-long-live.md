---
title: RAG要死掉了么？
toc: true
date: 2024-05-01
tags: [RAG,大模型,长上下文,检索增强生成]
categories: [人工智能]
description: 长上下文 LLM 的出现被一些人视为 RAG要死掉了。真相确实如此么？
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

The advent of long-context LLM is seen by some as the death of RAG. Are we really sure that is the case?
长上下文 LLM 的出现被一些人视为 RAG 之死。我们真的确定是这样吗？

LLMs can sometimes provide wrong answers. One of the main motivations is the information to answer the question is either absent in the original training set or successive to the data of training. The Retrieval Augmented Generation (RAG) augments the prompt with external information mitigating this behavior.
LLMs 有时会提供错误的答案。其中一个主要原因是，原始训练集中不存在回答问题的信息，或者训练数据是连续的。检索增强一代（RAG）通过外部信息来增强提示，从而减少了这种行为。

Long-context LLMs can access the prompt whole corpus of documents or even a book. Different researchers are questioning the future of RAG. If an LLM can ingest in the prompt all the necessary knowledge and retrieve it by itself, while it needs an external retrieval?
长语境 LLMs 可以访问提示整个语料库的文档，甚至是一本书。不同的研究人员都在质疑 RAG 的未来。如果 LLM 可以在提示中摄取所有必要的知识并自行检索，那么它还需要外部检索吗？

Moreover, AI regulations are on the way, we need to know how RAGs are secure, how they can identify the relevant information, and help the LLM to reduce its bias or not. Therefore, can RAG evolve to take into account these needs and resist long-context LLMs?
此外，人工智能法规即将出台，我们需要了解 RAG 如何确保安全，如何识别相关信息，并帮助 LLM 减少偏差。因此，RAG 能否进化到兼顾这些需求并抵御长语境 LLMs 呢？

In this article, we discuss what RAG is, what its advantages and disadvantages are, the impact of long-context LLM, and what the future holds for RAG.
在本文中，我们将讨论什么是 RAG、它的优缺点、长语境 LLM 的影响以及 RAG 的未来。

Index of the article 文章索引
What is the RAG anyway?
RAG 到底是什么？
Challenges to the RAG paradigm
对 RAG 模式的挑战
Why RAG is still relevant
为什么 RAG 仍有现实意义
The future of the RAG
RAG 的未来
Parting thoughts 临别赠言
TL;DR 简要说明
References 参考资料
What is the RAG anyway?
RAG 到底是什么？
is it RAG still alive?
Photo by Marten Newhall on Unsplash
照片由 Marten Newhall 在 Unsplash 上拍摄
In the past two years, we have seen an explosion of Large Language Models, both closed-source and open-source. ChatGPT can be seen as the watershed where LLMs went from being a research product to a consumer product. With their rapid adoption for various applications, it has been noted that LLMs are not without flaws.
在过去的两年中，我们看到了大型语言模型的爆炸式增长，包括闭源模型和开源模型。ChatGPT 可以看作是 LLMs 从研究产品变为消费产品的分水岭。随着它们在各种应用中的迅速普及，人们注意到 LLMs 并非没有缺陷。

A Requiem for the Transformer?
变形金刚的安魂曲？
Will be the transformer the model leading us to artificial general intelligence? Or will be replaced?
变压器将是引领我们走向人工通用智能的模型吗？还是会被取代？
towardsdatascience.com

One of the most observed problems is that LLMs tend to hallucinate. Hallucination is defined as the generation of content that is nonsensical or unfaithful to the provided question. The problem is exacerbated by the fact that LLMs sound authoritative and in some cases, only additional research can show that the generated content is incorrect. In addition, generalist models (the most popular ones) have a greater tendency to hallucinate than task-specific models.
观察到最多的问题之一是 LLMs 往往会产生幻觉。幻觉的定义是生成无意义或不符合所提供问题的内容。由于 LLMs 听起来具有权威性，而且在某些情况下，只有额外的研究才能证明所生成的内容是错误的，这就加剧了问题的严重性。此外，通用模型（最流行的模型）比特定任务模型更容易产生幻觉。

is it RAG still alive?
image source: here 图片来源：此处
Especially for knowledge-intensive tasks, a model that could access external knowledge would be favored, producing more reliable and factually consistent answers. To mitigate hallucinations, in 2020 researchers at META proposed Retrieval Augmented Generation (RAG).
特别是在知识密集型任务中，能够获取外部知识的模型将更受青睐，从而产生更可靠、更符合事实的答案。为了减少幻觉，META 的研究人员在 2020 年提出了 "检索增强生成"（RAG）方案。

Retrieval Augmented Generation (RAG) architecture, an end-to-end differentiable model that combines an information retrieval component (Facebook AI’s dense-passage retrieval system) with a seq2seq generator (our Bidirectional and Auto-Regressive Transformers [BART] model). (source)
Retrieval Augmented Generation (RAG) 架构是一个端到端的可微分模型，它将信息检索组件（Facebook AI 的密集通道检索系统）与 seq2seq 生成器（我们的双向和自回归变换器 [BART] 模型）结合在一起。( 来源)

In short, without the need to have to retrain the entire model, the LLM can access some external knowledge and use it efficiently for response generation. When a user asks the model a question, the RAG finds the relevant documents and these are concatenated to the ‘input prompt. The model thus generates the answer and considers the found context.
简而言之，LLM无需重新训练整个模型，就能获取一些外部知识，并有效地用于生成回复。当用户向模型提问时，RAG 会查找相关文档，并将这些文档与 "输入提示 "连接起来。这样，模型就能生成答案，并考虑到找到的上下文。

is it RAG still alive?
image source: here 图片来源：此处
The so-called Naive RAG (simplest form of RAG) follows three simple steps: indexing, retrieval, and generation. In the first step, the various documents are divided into chunks and are transformed into a vector representation by an embedding model. Once a user query arrives, it is embedded in a vector representation, it is then computer the similarity scores between the query vector and the vectors that were previously stored. The vectors that have the most similarity are selected and the corresponding chunks are embedded in a coherent prompt. This prompt is then fed to the LLM for response generation.
所谓的 Naive RAG（RAG 的最简单形式）遵循三个简单步骤：索引、检索和生成。在第一步中，各种文档被分成若干块，并通过嵌入模型转换成向量表示。用户查询到达后，会被嵌入到向量表示中，然后通过计算机计算查询向量与之前存储的向量之间的相似度得分。选出相似度最高的向量，并将相应的块嵌入一个连贯的提示中。然后，将该提示输入 LLM 以生成回复。

is it RAG still alive?
image source: here 图片来源：此处
Moreover, the RAG method also solves other known problems of LLMs:
此外，RAG 方法还解决了 LLMs 的其他已知问题：

Maintain up-to-date knowledge. In fact, embedding in RAG is much faster and more cost-effective than having to re-train an LLM.
保持最新知识。事实上，嵌入 RAG 比重新培训 LLM 要快得多，也更具成本效益。
Limited memorization for less frequent entities. RAG allows finding specific documents for entities that are underrepresented in the LLM’s training dataset.
对频率较低的实体进行有限记忆。RAG 可以为 LLM 的训练数据集中代表性不足的实体查找特定文件。
Leaking private training data. Several studies show that LLMs can leak private data; the RAG allows greater control over what data is used in generating and finding the source of the problem in case of leakage.
泄漏私人训练数据。多项研究表明，LLMs 可能会泄露私人数据；RAG 可以更好地控制生成数据的用途，并在发生泄露时找到问题的根源。
These advantages and an objective improvement in the performance of LLMs+RAGs in question answering prompted rapid adoption of the system by researchers and companies.
这些优势以及 LLMs+RAG 在答题性能方面的客观改进，促使研究人员和公司迅速采用该系统。

If the RAG has all these advantages, why some resarchers are saying the RAG is is doomed to extinction?
既然 RAG 有这些优点，为什么有些研究人员说 RAG 注定要灭绝呢？

In the next section we will discuss what challenges RAG faces and whether these challenge its existence in the future.
在下一节中，我们将讨论 RAG 面临的挑战，以及这些挑战是否会对其未来的存在构成挑战。

Challenges to the RAG paradigm
对 RAG 模式的挑战
is it RAG still alive?
Photo by Jukan Tateisi on Unsplash
照片由 Jukan Tateisi 在 Unsplash 上拍摄
RAG has been so extensively successful that many companies have adopted vector databases, where carriers are stored. In the same way, an ecosystem of start-ups dedicated to enabling the storage of these vectors in the cloud has grown. With its success, the interest of researchers has also grown, and several studies have focused on investigating potential problems and pitfalls of RAG.
由于 RAG 取得了巨大成功，许多公司都采用了载体数据库来存储载体。同样，致力于在云端存储这些载体的初创公司生态系统也在不断壮大。随着 RAG 的成功，研究人员的兴趣也与日俱增，多项研究都侧重于调查 RAG 的潜在问题和隐患。

Since RAGs’ systems are going into production it is important to discuss the impact on security and applications. Especially, at this moment when new regulations are approved and will affect the AI industry.
由于 RAGs 系统即将投入生产，因此讨论其对安全性和应用的影响非常重要。尤其是在新法规获得批准并将对人工智能行业产生影响的时刻。

In this section, we will discuss in detail these potential critical points:
在本节中，我们将详细讨论这些潜在的关键点：

Does the RAG make the LLMs more secure? Or it is more vulnerable?
RAG 是否使 LLMs 更安全？还是更加脆弱？
Does the RAG really retrieve the most important information? We have faith it does but is it really true?
RAG 真的能检索到最重要的信息吗？我们相信它能，但事实真的如此吗？
Long context-length models are on the way, are they wiping out RAGs? If the LLM can retrieve information by itself why do we need external components?
长上下文长度模型即将问世，它们会消灭 RAG 吗？如果 LLM 可以自行检索信息，为什么还需要外部组件？
Vector database security 矢量数据库安全
Embedding vectors are vectors of real numbers that look almost random to the human eye. Although these vectors correspond to sensitive data, they seem to respect a company’s privacy. Were they even saved in the cloud and someone manages to access the vector database, all they would get would be useless number vectors. Perhaps.
嵌入矢量是实数矢量，人眼看上去几乎是随机的。虽然这些向量对应的是敏感数据，但它们似乎尊重公司的隐私。如果它们被保存在云中，而有人设法访问矢量数据库，那么他们得到的将只是无用的数字矢量。也许吧。

Several studies show that an LLM with the right prompt can conduct data leakage, and in the case associated with a RAG, you can get from the model the documents (or chunks) used for generation.
一些研究表明，带有正确提示的 LLM 可以进行数据泄漏，而在与 RAG 相关的情况下，你可以从模型中获取用于生成的文档（或块）。

There is a more insidious way. In fact, having access to the embedding one can reconstruct the text.
还有一种更隐蔽的方法。事实上，只要获取了嵌入的内容，就可以重建文本。

Our method, Vec2Text, uses the difference between a hypothesis embedding and a ground-truth embedding to make discrete updates to the text hypothesis. (source)
我们的方法 Vec2Text 利用假设嵌入和地面真实嵌入之间的差异，对文本假设进行离散更新。( 来源)

So you simply optimize a model that takes an embedding vector, use a “hypothesis”, and check for similarity. You then use a model to correct the hypothesis until it is very close to the target embedding, by doing so you reconstruct the original text.
因此，您只需优化一个模型，该模型采用嵌入向量，使用 "假设"，并检查相似性。然后使用模型修正假设，直到非常接近目标嵌入，这样就能重建原文。

is it RAG still alive?
image source: here 图片来源：此处
If text is recoverable, there is a threat to privacy: a malicious user with access to a vector database, and text-embedding pairs from the model used to produce the data, could learn a function that reproduces text from embeddings. (source)
如果文本是可恢复的，那么隐私就会受到威胁：如果恶意用户可以访问矢量数据库，并从用于生成数据的模型中获得文本嵌入对，那么他就可以学习一个从嵌入中复制文本的函数。( 数据源)

Sensible information can be present in the vector databases, but we thought the transformation in a numeric representation made them safe. Instead, researchers found that this transformation is conservative and the information can be reconstructed. In other words, special attention should be paid to the privacy of these RAG vector databases. Just as we take care that raw documents are not accessible, their embedding vectors should also be protected
矢量数据库中可能存在合理的信息，但我们认为数字表示的转换使它们变得安全。相反，研究人员发现这种转换是保守的，信息可以被重建。换句话说，应该特别注意这些 RAG 向量数据库的隐私。正如我们要确保原始文档无法访问一样，它们的嵌入向量也应受到保护

The AI worm and the LLM leaf
人工智能蠕虫和 LLM 树叶
New research warns how a LLM can be poisoned and spread around
新研究警告 LLM 如何中毒并四处传播
levelup.gitconnected.com

Similarity measurement 相似性测量
When we talk about similarity scores we are talking about cosine similarity. Which is surprising. In fact, the RAG is the cooperation of two sophisticated models (an embedding model and an LLM), whereas to calculate similarity we use an extremely simple formula. Why?
当我们谈论相似性得分时，我们谈论的是余弦相似性。这令人惊讶。事实上，RAG 是两个复杂模型（嵌入模型和 LLM）的合作结果，而计算相似度时，我们使用的是一个极其简单的公式。为什么呢？

is it RAG still alive?
image source: here 图片来源：此处
Mainly because of storage cost, high computational efficiency, and good retrieval performance of cosine similarity. Also, there have been few studies that have investigated the impact of cosine similarity in retrieval.
这主要是因为余弦相似性具有存储成本低、计算效率高和检索性能好等优点。此外，研究余弦相似性在检索中的影响的研究也不多。

Yet some of its drawbacks are well known. For example, cosine similarity returns the same value regardless of the size of the vectors, as long as the angle between them is the same.
然而，它的一些缺点也是众所周知的。例如，无论向量的大小如何，只要它们之间的角度相同，余弦相似度就会返回相同的值。

Recent studies show instead, that embedding model architecture and embedding normalizations impact the similarity obtained with cosine similarity. So depending on training or preprocessing choices using cosine similarity may not return the most relevant documents.
最近的研究表明，嵌入模型结构和嵌入归一化反而会影响余弦相似度的相似性。因此，根据训练或预处理的选择，使用余弦相似度可能无法返回最相关的文档。

is it RAG still alive?
image source: here 图片来源：此处
Cosine Similarity and Embeddings Are Still in Love?
余弦相似性和嵌入式还相爱吗？
Cosine similarity is the most used method, but it is really the best?
余弦相似度是最常用的方法，但它真的是最好的吗？
levelup.gitconnected.com

Increase in the LLM context length
增加 LLM 上下文长度
Gemini 1.5 Pro comes with a standard 128,000 token context window. But starting today, a limited group of developers and enterprise customers can try it with a context window of up to 1 million tokens via AI Studio and Vertex AI in private preview.
Gemini 1.5 Pro 配备了标准的 128,000 代币上下文窗口。但从今天起，少数开发人员和企业客户可以通过 AI Studio 和 Vertex AI 在私人预览版中尝试使用高达 100 万个代币的上下文窗口。

The authors say that while a context of 1M tokens shows great results, they are still optimizing the model. Indeed, they are trying to optimize latency, computational requirements, and results. Nevertheless, the announcement led to an earthquake.
作者说，虽然 100 万个代币的上下文显示了很好的结果，但他们仍在对模型进行优化。事实上，他们正在努力优化延迟、计算要求和结果。尽管如此，这一消息还是引发了一场地震。

Obviously, such a vast context length piqued users’ interest (as well as allowing Google to brag about it). In fact, the wider the context length, the more information the model can attend to. Such a monstrous context length means that Google’s model can process: “1 hour of video, 11 hours of audio, codebases with over 30,000 lines of code or over 700,000 words.”
显然，如此长的上下文长度引起了用户的兴趣（同时也让谷歌得以炫耀）。事实上，上下文长度越长，模型能够处理的信息就越多。如此巨大的上下文长度意味着谷歌的模型可以处理"1小时的视频、11小时的音频、超过3万行代码或超过70万字的代码库"。

So the model could then conduct more complex reasoning, learn new skills more easily, and be more reliable and factually correct.
这样，模型就能进行更复杂的推理，更容易学习新技能，而且更可靠、更符合事实。

Speak to me: How many words a model is reading
说给我听模特读了多少字
Why and how to overcome the inner limit of a Large Language Model
为什么以及如何克服大型语言模型的内部限制
towardsdatascience.com

In general, after Google’s presentation, some researchers said, “Long context will replace RAG.” In short, the major arguments for this theory are:
总的来说，在谷歌的演讲之后，一些研究人员说："长语境将取代 RAG"。简而言之，这一理论的主要论点是：

Cost per token. RAG is cheap and fast, but the cost per token will go down with time and therefore models with long context will be more widespread.
每个令牌的成本。RAG 价格便宜，速度快，但随着时间的推移，每枚令牌的成本会下降，因此具有长背景的模型会更加普及。
User case scenarios. Most real-case scenarios are covered by 1M tokens, so we do not need RAGs for the few cases reaming out.
用户案例场景。100 万个代币已经涵盖了大多数真实案例，因此我们不需要 RAG 来处理少数案例。
KV cache. With the KV cache, one must read the input once, and subsequent queries will reuse the KV cache for the computation of the attention product. This will make even a long-context LLM fast.
KV 缓存。有了 KV 缓存，我们只需读取一次输入，随后的查询将重复使用 KV 缓存来计算注意力积。这样，即使是长上下文 LLM 也会很快。
Speed. Such a long context length is slow, but according to many, it will get faster quickly. Indeed, technology improves quickly.
速度。如此长的上下文长度是比较慢的，但许多人认为，它很快就会变得更快。的确，技术进步很快。
Accuracy. A model that natively interleaves retrieval/generation via its attention layers has a qualitatively superior response to naive RAG. It finds information in the context and processes it at the same time.
准确性。一个通过注意力层将检索/生成交错在一起的模型，其反应在质量上要优于天真的 RAG。它能在上下文中找到信息，并同时对其进行处理。
As a last point, another reason why the RAGs are born is that early LLMs had a short context length. RAG was helping to sort out information, leaving out irrelevant ones and providing the important ones to the prompt (prompt augmentation).
最后一点，RAG 诞生的另一个原因是早期的 LLMs 上下文长度较短。RAG 可以帮助整理信息，剔除无关信息，将重要信息提供给提示信息（提示增强）。

One of the primary challenges in early stage RAG, which leverages prompt augmentation, is the inherent context length limitation of the generators. The research advancements in prompt compression and long-context support have partially mitigated this challenge. (source)
利用提示增强技术的早期 RAG 所面临的主要挑战之一是生成器固有的上下文长度限制。提示语压缩和长语境支持方面的研究进展部分缓解了这一挑战。(资料来源）

Therefore, for many authors, the long context is considered the main challenge to the future of RAG.
因此，许多作者认为，长期的背景是 RAG 未来面临的主要挑战。

Why RAG is still relevant
为什么 RAG 仍有现实意义
is it RAG still alive?
Photo by Fauzan Saari on Unsplash
照片由 Fauzan Saari 在 Unsplash 上拍摄
In the previous sections, we discussed the advantages of RAG: increased safety, speed, and accuracy in finding information, and reduction of LLM hallucination. Then, we saw that some studies question these advantages, and the advent of the long-context LLM questions the usefulness of the LLM+RAG system.
在前面的章节中，我们讨论了 RAG 的优势：提高查找信息的安全性、速度和准确性，以及减少 LLM 幻觉。然后，我们看到一些研究对这些优势提出了质疑，而长语境 LLM 的出现则对 LLM+RAG 系统的实用性提出了质疑。

Without a doubt, long context is an advancement for LLMs, but is it really an existential threat to RAG?
毫无疑问，长语境是 LLMs 的进步，但它真的会威胁到 RAG 的生存吗？

In this section, we will discuss why RAG is not doomed and indeed long context opens up interesting prospects for the future of RAG. We will discuss these points:
在本节中，我们将讨论为什么 RAG 并非注定要失败，事实上，长期的背景为 RAG 的未来开辟了有趣的前景。我们将讨论以下几点：

Are we sure we are making the right comparison? Naive RAG is not outdated and we are using now more sophisticated solutions
我们确定我们的比较是正确的吗？简单的 RAG 并没有过时，我们现在使用的是更先进的解决方案
Is it long-context LLM adapted for all cases? What for specialized domains?
长语境 LLM 是否适用于所有情况？对于专业领域呢？
Does long-context LLM have a higher cost? What about latency in inference?
长上下文 LLM 的成本是否更高？推理的延迟如何？
Do LLMs use Long-Context efficiently? Or are they just claims from AI companies?
LLMs 是否有效地使用了长语境？还是只是人工智能公司的说法？
Interpretability and safety are a must-have now, how are long-context LLMs and RAGs related to that?
现在，可解释性和安全性是必备条件，那么长语境 LLMs 和 RAG 与此有关吗？
Can there be instead possible coexistence of long-context LLMs and RAGs?
长语境 LLMs 和 RAG 能否共存？
Naive RAG has been substituted by advanced solutions
先进的解决方案取代了原始的 RAG
The naive RAG has low accuracy and thus finds misaligned chunks. Paradoxically, finding the wrong context can lead to hallucinations in the generation. Also, redundant, repetitive, or query-irrelevant chunks may be found while some relevant chunks may not be found.
天真 RAG 的准确率较低，因此会发现错误对齐的语块。矛盾的是，找到错误的上下文可能会导致生成幻觉。此外，冗余、重复或与查询无关的语块可能会被找到，而一些相关的语块则可能找不到。

is it RAG still alive?
image source: here 图片来源：此处
Today, systems using RAG exploit pre-retrieval and post-retrieval optimization. For example, indexing is optimized and metadata is often added. Also, retrieval today is conducted not only by embedding but also by hybrid search (contextual and semantic information). The retrieved documents then are reordered by a re-ranker, so that those most relevant to the query are identified.
如今，使用 RAG 的系统利用检索前和检索后优化。例如，对索引进行优化，并经常添加元数据。此外，如今的检索不仅通过嵌入进行，还通过混合检索（上下文和语义信息）进行。然后，检索到的文件将由重新排序器重新排序，以便找出与查询最相关的文件。

Therefore, advanced RAGs are much more robust and reliable than long-context LLM.
因此，先进的 RAG 比长上下文 LLM 更稳健可靠。

Domain adaptation and continuous learning
领域适应和持续学习
RAG is like giving a model a textbook for tailored information retrieval, perfect for specific queries. On the other hand, FT is like a student internalizing knowledge over time, better for replicating specific structures, styles, or formats. (source)
RAG 就像是给模型提供了一本定制信息检索的教科书，非常适合特定的查询。另一方面，FT 就像一个学生随着时间的推移不断内化知识，更适合复制特定的结构、风格或格式。( 资料来源)

However, in naive RAG the embedding model is frozen, but some dynamic systems and models are fine-tuned. Especially for specialized domains it is possible to obtain embeddings that are tailored to the specific field. Especially for technical fields a fine-tuned RAG performs better than a generic model, this is dramatically highlighted for complex queries.
然而，在天真的 RAG 中，嵌入模型是冻结的，但某些动态系统和模型是微调的。特别是在专业领域，有可能获得适合特定领域的嵌入模型。特别是在技术领域，经过微调的 RAG 比通用模型的性能更好，这在复杂查询中表现得尤为突出。

The transformer by its nature does not allow continuous learning, so it would be necessary to conduct some fine-tuning. First, for specific domains (medicine, finance, and so on) this has a much lower cost. In fact, it is much cheaper to fine-tune an embedding model (about 100M parameters) than an LLM (billions of parameters). Second, in RAG fine-tuning is not strictly necessary, new documents can be directly embedded and LLM will use them to generate.
转换器的性质决定了它不允许持续学习，因此有必要进行一些微调。首先，对于特定领域（医学、金融等）来说，微调的成本要低得多。事实上，微调一个嵌入模型（约 1 亿个参数）要比微调 LLM 模型（数十亿个参数）便宜得多。其次，在 RAG 中，微调并不是绝对必要的，新的文档可以直接嵌入，LLM 将使用它们来生成。

In any case, RAG and fine-tuning are not mutually exclusive. So it is possible to fine-tune a model on a specific domain (e.g., medicine) and at the same time connect it to an RAG. This allows for superior performance, further reducing hallucinations, and allowing the model to have up-to-date knowledge.
无论如何，RAG 和微调并不相互排斥。因此，可以对特定领域（如医学）的模型进行微调，同时将其连接到 RAG。这样就能获得更优越的性能，进一步减少幻觉，并使模型拥有最新的知识。

is it RAG still alive?
image source: here 图片来源：此处
Thus, a long-context LLM cannot be fine-tuned (except at great cost) so for specialized domains, a small LLM with a RAG is clearly the best choice.
因此，长上下文 LLM 无法进行微调（除非花费巨资），所以对于专业领域来说，带有 RAG 的小型 LLM 显然是最佳选择。

Google Med-PaLM: The AI Clinician
Google Med-PaLM：人工智能临床医生
Google's new model is trained to answer medical questions. How?
谷歌的新模型经过训练，可以回答医疗问题。怎么训练？
towardsdatascience.com

Speed, Cost, and Latency 速度、成本和延迟
As has been noted, such context length has a cost on performance. The time required to parse a document (or corpus) increases with the number of tokens that are provided: 160K tokens take more than twenty seconds, rising above 60 for more than 800k.
如前所述，这种上下文长度会影响性能。解析文档（或语料库）所需的时间会随着提供的标记数量而增加：16 万个词组需要 20 多秒钟，超过 80 万个词组则需要 60 多秒钟。

Similarly, the cost increases, both noticed by Google and by potential users:
同样，成本也会增加，谷歌和潜在用户都会注意到这一点：

For example, retrieving 1 million tokens of datasets at a rate of $0.0015 per 1000 tokens could lead to substantial expenses, potentially amounting to $1.50 for a single request. This cost factor renders such high expenditures impractical for everyday utilization, posing a significant barrier to widespread adoption. (source)
例如，以每 1000 个代币 0.0015 美元的费率检索 100 万个代币的数据集，可能会导致巨额支出，单次请求可能高达 1.50 美元。这一成本因素使得如此高昂的支出在日常使用中变得不切实际，对广泛采用构成了重大障碍。( 来源)

Clearly, both cost and time are critical for a user who must conduct several daily searches or must ask a large number of questions on a large corpus. Thus, both in terms of time and cost, it is cheaper to train one’s own model or create an RAG.
显然，对于每天必须进行多次搜索或必须在大型语料库中提出大量问题的用户来说，成本和时间都是至关重要的。因此，就时间和成本而言，训练自己的模型或创建 RAG 都更为经济。

The quality of the answer and the quality of the data
答案的质量和数据的质量
The official model report states that Gemini introduced the “needle-in-a-haystack,” a new method to appreciate the retrieval capability of their model. Google states that its model achieves 100 percent recall for 500K tokens and 99.7 percent when scaling to 1M tokens. According to the authors, Gemini has an outstanding ability in retrieval when compared with long context:
官方模型报告指出，Gemini 引入了 "大海捞针 "这一新方法，以了解其模型的检索能力。谷歌指出，其模型在检索 500K 标记时的召回率为 100%，在扩展到 100 万标记时召回率为 99.7%。作者认为，与长上下文相比，Gemini 的检索能力非常突出：

Scaling to millions of tokens, we find a continued improvement in predictive performance, near perfect recall (>99%) on synthetic retrieval tasks, and a host of surprising new capabilities like in-context learning from entire long documents. (source)
将其扩展到数百万个 token 时，我们发现其预测性能持续提高，在合成检索任务中的召回率接近完美（>99%），并具有大量令人惊讶的新功能，例如从整个长文档中进行上下文学习。( 来源)

is it RAG still alive?
image source: here 图片来源：此处
For Google, this translates into higher accuracy in question answering when compared with other LLMs. For the authors, this happens because Gemini is able to resolve reference expressions and conduct reasoning across long-distance dependencies
对谷歌来说，这意味着与其他 LLMs 相比，问题解答的准确性更高。对于作者来说，这是因为双子座能够解决引用表达式问题，并在远距离依赖关系中进行推理

is it RAG still alive?
image source: here 图片来源：此处
These reports seem to be confirmed by several users who have tested the model’s capabilities in a long context. For example, one user states that Gemini found the changes he had made to The Great Gatsby before uploading. Another is that the model was able to answer specific questions after it had fed an entire biology textbook into Gemini.
这些报告似乎得到了一些用户的证实，他们对该模型的功能进行了长时间的测试。例如，一位用户说，Gemini 在上传之前就发现了他对《了不起的盖茨比》所做的修改。另一位用户则表示，在将整本生物学教科书输入双子座后，该模型能够回答特定的问题。

Nevertheless, skepticism remains, because a short time ago this article showed that models have a greater ability to find information that is found in the middle of the context length (showing a typical u-shaped curve):
尽管如此，怀疑的声音依然存在，因为不久前这篇文章显示，模型发现上下文长度中间信息的能力更强（呈现典型的 U 形曲线）：

is it RAG still alive?
image source: here 图片来源：此处
Certainly, Gemini has an advantage when it comes to answering questions about an entire book or summarizing it. But organizations often have many more documents (well over a million tokens) and you can’t enter the entire Wikipedia at once. Also, there are reports that Gemini still hallucinates from time to time (number of pages and other details).
当然，在回答有关整本书的问题或对其进行总结时，Gemini 具有优势。但是，组织机构往往有更多的文档（远远超过一百万个代币），你不可能一次性输入整个维基百科。此外，有报告称，Gemini 还时不时会出现幻觉（页数和其他细节）。

Also, most of the data is often unstructured data and Gemini seems to struggle with it. So once the work of cleaning this data is done, you might as well put it in an RAG and use a smaller model.
此外，大部分数据通常都是非结构化数据，Gemini 似乎很难处理这些数据。因此，一旦完成了这些数据的清理工作，不妨将其放入 RAG 中并使用一个较小的模型。

In addition, any organization also has other types of data such as tabular data, graphs, images, and time series. All these data have structures that LLMs do not capture perfectly. So LLM can be a central element of a company’s strategy but it must be accompanied by a structure around it to be useful in real-world case scenarios.
此外，任何组织还拥有其他类型的数据，如表格数据、图表、图像和时间序列。所有这些数据都具有 LLMs 无法完美捕捉的结构。因此，LLM 可以成为公司战略的核心要素，但必须辅以相应的结构，才能在实际案例中发挥作用。

Do Really Long-Context LLMs Exist
真正的长语境 LLMs 是否存在
Long-context LLMs are the topic of the moment, but beyond companies' claims, it is true?
长语境 LLMs 是当下的热门话题，但除了公司的说法之外，它是真的吗？
levelup.gitconnected.com

Interpretability and safety
可解释性和安全性
LLM suffers from hallucinations, and increasing the context length reduces the problem but does not eliminate it. There are fields where this can have dramatic effects (e.g., medicine or finance). If LLMs enter a decision-making field they have to understand the internal reasoning. An LLM is effectively a black box, and accessing the various sections of a long context length is a process that remains opaque.
1001#会产生幻觉，增加上下文长度会减少问题，但不会消除幻觉。有些领域（如医学或金融）会产生巨大影响。如果 LLMs 进入决策领域，他们就必须了解内部推理。LLM 实际上是一个黑盒子，访问长上下文长度的各个部分是一个仍然不透明的过程。

For an RAG, on the other hand, one can track the documents used to generate the response, thus making the process much more inspectable and observable (without additional cost).
另一方面，对于 RAG 而言，我们可以跟踪用于生成响应的文件，从而使流程更易于检查和观察（无需额外成本）。


image source: here 图片来源：此处
Long context and RAG can coexist
长语境和 RAG 可以共存
“RAG (retrieval-augmented generation) isn’t done for, even though we can handle 1M or more tokens in context now. In fact, RAG has some nice properties that can enhance (and be enhanced by) long context.” — Oriol Vinyals, source
"RAG（检索增强生成）并不是一劳永逸的，尽管我们现在可以处理 100 万或更多的上下文标记。事实上，RAG 有一些很好的特性，可以增强（并被增强）长语境"。- Oriol Vinyals，来源

RAG can help a model that has a long context solve hallucination problems, maintain traceability, extend it beyond 1M tokens, and work with unstructured data. Actually, long context also benefits RAG:
RAG 可以帮助具有长上下文的模型解决幻觉问题，保持可追溯性，将其扩展到超过 100 万个令牌，并处理非结构化数据。事实上，长上下文也有利于 RAG：

Developers have to worry less about chunking. Chunking size is one of the pain points of RAG, choosing chunk size and choosing metadata is an art and sometimes requires multiple attempts.
开发人员不必担心分块问题。分块大小是 RAG 的痛点之一，选择分块大小和元数据是一门艺术，有时需要多次尝试。
Better chronology for conversational agents. Another issue is how much context should be provided to the model in the prompt for a query. For example, if the agent has to enter previous interactions with the user (plus several documents into the prompt), one can easily end up in overflow. Instead, with a long context you can easily keep the conversation history while the RAG focuses on finding supporting documents.
为对话式代理提供更好的时间顺序。另一个问题是在查询提示中应向模型提供多少上下文。例如，如果代理必须在提示中输入以前与用户的交互（以及若干文档），就很容易导致溢出。相反，如果提供较长的上下文，则可以在 RAG 专注于查找支持文档的同时轻松保留对话历史。
Improved performance on different tasks. For example, there will be a great advantage in summarization. The RAG could find several documents and LLM nimbly summarized dozens (if not hundreds) of them. The same for question answering, often several chunks of a document are needed to answer a question about a single document (the elements for the answer may be scattered in various sections of a document). The model could thus make a chain of thought in which each step is associated with a different chunk.
提高不同任务的性能。例如，在总结方面将有很大优势。RAG 可以找到多个文档，并 LLM 灵活地对其中的几十个（甚至上百个）文档进行总结。问题解答也是如此，要回答一个关于单个文档的问题，往往需要几大块文档（答案的元素可能分散在文档的不同部分）。因此，该模型可以形成一个思维链，其中每一步都与不同的大块相关联。
Therefore, since there are possibilities to integrate both long context and RAG, in the next section we will discuss how RAG will evolve
因此，由于存在将长篇背景和 RAG 结合起来的可能性，我们将在下一节讨论 RAG 将如何发展

The future of the RAG
RAG 的未来
is it RAG still alive?
Photo by Drew Beamer on Unsplash
照片由 Drew Beamer 在 Unsplash 上拍摄
In the previous section, we have seen that RAG and long-context LLM can coexist. Indeed, long-context is not the perfect solution for all business and user needs.
在上一节中，我们看到 RAG 和长语境 LLM 可以共存。事实上，长上下文并非满足所有业务和用户需求的完美解决方案。

However, the arrival of long-context LLMs will require an evolution of RAG, new methods, and new architectures that will soon be unveiled or are part of changes already underway. These strategies will seek to make the entire system more efficient. Since RAG is a more agile and lightweight system than LLMs, it is easier to experiment with new solutions. Therefore, an explosion of new methods can be expected in the coming months.
然而，长语境 LLMs 的到来将需要 RAG、新方法和新架构的进化，这些新方法和新架构很快就会亮相，或者是已经在进行的变革的一部分。这些战略将努力提高整个系统的效率。由于 RAG 是一个比 LLMs 更敏捷、更轻量级的系统，因此更容易尝试新的解决方案。因此，在未来几个月内，新方法将层出不穷。

Here, we will discuss potential evolution in the RAG environment:
在此，我们将讨论 RAG 环境中的潜在演变：

How chunking and retrieval will evolve?
分块和检索将如何发展？
Can we have a more intelligent retrieval?
我们能进行更智能的检索吗？
Can KV caching be integrated with RAG?
KV 缓存能否与 RAG 集成？
What about RAG 2.0? RAG 2.0 如何？
Chunking and retrieval 分块和检索
As mentioned both chunking and retrieval are components of RAG that are already undergoing evolution. For example, increasing the contest length of LLMs means that larger chunks can be retrieved. This is pushing to have embedding models that also have a larger context length. In fact, as seen from the MTEB leaderboard there are already models that take a context length of 32K with a substantial improvement in their embedding capabilities.
如前所述，分块和检索都是 RAG 的组成部分，目前已在不断发展。例如，增加 LLMs 的竞赛长度意味着可以检索到更大的分块。这就推动了嵌入模型也具有更大的上下文长度。事实上，从 MTEB 排行榜上可以看到，已经有一些模型可以使用 32K 的上下文长度，从而大大提高了嵌入能力。

is it RAG still alive?
MTEB leaderboard shows how 4 out of 5 five best models have a context length of 32K. screen by the author
MTEB 排行榜显示，在 5 个最佳模型中，有 4 个模型的上下文长度为 32K。 作者截屏
The context length will also likely push for an alternative strategy. For example, small-to-big retrieval is a method in which small chunks are indexed and found, but these small chunks refer to larger documents, and ultimately it is these larger chunks that are fed to the model. Or you index and conduct embedding of the document summary, retrieve the document, and feed it to the LLM. This technique is compatible with embedders that have small context lengths and when speed is a priority.
上下文的长度也可能会推动另一种策略。例如，从小到大检索法是一种索引和查找小块文档的方法，但这些小块文档指向的是大块文档，最终是这些大块文档被输入到模型中。或者你对文档摘要进行索引和嵌入，检索文档，并将其输入 LLM 。这种技术适用于上下文长度较小、速度优先的嵌入。

Alternatively, RAG chunk-free or landmark embedding is discussed today. In this case, landmark tokens (LMKs) are added and then the embedding is conducted with a sliding window. The algorithm is multi-stage and exploits a position-aware function to find information that is included in multiple sentences. This system was designed with long-context language modeling in mind and applied to an arbitrary context.
另外，今天讨论的是 RAG 无块嵌入或地标嵌入。在这种情况下，先添加地标标记（LMK），然后使用滑动窗口进行嵌入。该算法分为多个阶段，利用位置感知功能查找包含在多个句子中的信息。该系统在设计时考虑到了长语境语言建模，并适用于任意语境。

is it RAG still alive?
image source: here 图片来源：此处
Intelligent routing for RAG
RAG 智能路由
Certainly, both the cost of generation and the generation time will be reduced, but when is not yet predictable. So a user will have to decide whether he needs a long context or not. For example, depending on a query a router might decide whether the RAG needs to retrieve a few chunks or entire documents. Summarization would benefit by entire documents but multi-part questions could be solved by more sophisticated pipelines that include chain-of-thoughts, retrieval, and reasoning in an alternating fashion.
当然，生成成本和生成时间都会减少，但何时减少还无法预测。因此，用户必须决定是否需要长上下文。例如，路由器可能会根据查询决定 RAG 需要检索的是几块内容还是整个文档。整篇文档将有利于归纳总结，但多部分问题可以通过更复杂的管道来解决，其中包括思维链、检索和推理交替进行的方式。

RAG + KV cache RAG + KV 缓存
For some, KV caching seems like the panacea to all the ills of long-context LLMs. Simply put, a KV cache stores pre-existing key and query vectors for an attention layer. This serves to avoid recomputing these activations for the entire text sequence during response generation.
对某些人来说，KV 缓存似乎是解决长上下文 LLMs 所有弊病的灵丹妙药。简单地说，KV 缓存为注意力层存储了预先存在的关键字和查询向量。这样可以避免在生成响应时为整个文本序列重新计算这些激活。

is it RAG still alive?
image source: here 图片来源：此处
The KV cache however requires a significant amount of GPU memory. It also requires dependencies and complex structures to be effective. Also, it is fine with a single document, but it is very complex when the corpus is large.
然而，KV 缓存需要大量的 GPU 内存。它还需要依赖关系和复杂的结构才能有效。此外，它在处理单个文档时没有问题，但当语料库庞大时就会变得非常复杂。

Therefore retrieval augmented caching has been proposed, where documents are found and loaded into the KV cache, speeding up generation.
因此，有人提出了检索增强缓存，即找到文档并将其加载到 KV 缓存中，从而加快生成速度。

Small models and RAG 2.0
小型模型和 RAG 2.0
As mentioned earlier RAG is a rapidly evolving process. Today, almost all use a more sophisticated and advanced form of the naive RAG. Often these systems are built around small LLMs (even less than 10B parameters), so it is easy to retune them with new components quickly and inexpensively. In addition, this allows so-called end-to-end fine-tuning, where the entire system (language model and retriever) is optimized as one system.
如前所述，RAG 是一个快速发展的过程。如今，几乎所有的 RAG 系统都采用了更复杂、更先进的天真 RAG 形式。通常，这些系统都是围绕小 LLMs（甚至少于 10B 个参数）构建的，因此很容易快速、低成本地使用新组件对其进行重新调整。此外，这还允许所谓的端到端微调，即整个系统（语言模型和检索器）作为一个系统进行优化。

is it RAG still alive?
image source: here 图片来源：此处
Language models struggle with knowledge-intensive tasks because they can only rely on the information they received during the pre-training phase. On the other hand, the model learns general knowledge and skills. When connected to the RAG, the model is not specialized for the new task or how to use the context it receives. When an LLM is intensively used for specialized domains much of the acquired knowledge and skills are less important:
语言模型很难完成知识密集型任务，因为它们只能依靠在预训练阶段获得的信息。另一方面，模型学习的是一般知识和技能。当连接到 RAG 时，模型并没有针对新任务或如何使用所接收的上下文进行专门训练。当 LLM 被大量用于专业领域时，大部分已获得的知识和技能就不那么重要了：

In these settings, general knowledge reasoning is less critical but instead, the primary goal is to maximize accuracy based on a given set of documents. Indeed, adapting LLMs to the specialized domains (e.g., recent news, enterprise private documents, or program resources constructed after the training cutoff) is essential to many emerging applications. (source)
在这些情况下，常识推理就不那么重要了，而主要目标是根据给定的文档集最大限度地提高准确率。事实上，让 LLMs 适应专业领域（如最近的新闻、企业私有文档或训练截止后构建的程序资源）对于许多新兴应用来说至关重要。( 来源)

Therefore, the best option is to optimize the whole system, including the LLM. Now this is possible with small models, whereas fine-tuning huge models would cost an enormous amount of money. The system becomes more robust because it allows it to be optimized to take advantage of external information.
因此，最好的办法是优化整个系统，包括 LLM 。现在，通过小型模型就可以做到这一点，而对大型模型进行微调则需要花费巨额资金。由于可以利用外部信息进行优化，系统变得更加稳健。

is it RAG still alive?
image source: here 图片来源：此处
The good thing is that RAG is a more flexible system than people think. We can optimize it to find specialized information at the domain but we can also optimize it for reasoning tasks. In fact, in this case, we alternate between reasoning and retrieval steps to be able to solve a task:
好在 RAG 是一个比人们想象的更加灵活的系统。我们可以对其进行优化，以查找领域内的专业信息，但也可以针对推理任务对其进行优化。事实上，在这种情况下，我们需要交替使用推理和检索步骤来完成任务：

is it RAG still alive?
image source: here 图片来源：此处
Follow the Echo: How to Get a Good Embedding from your LLM
跟随回声：如何从 LLM 中获得良好的嵌入效果
How to overcome the limits of Autoregressive Models for embedding
如何克服自回归模型在嵌入方面的局限性
levelup.gitconnected.com

Parting thoughts 临别赠言
is it RAG still alive?
Photo by Saif71.com on Unsplash
照片由 Saif71.com 在 Unsplash 上发布
The bus did not kill the car. Increased capacity is always at the cost of decreased flexibility. The long-context LLM is certainly a great technological advancement and a point of pride for Google. Certainly in this aspect, Gemini is currently superior to Claude and GPT4. Comparing Gemini and RAG, on the other hand, makes much less sense.
公共汽车并没有杀死汽车。容量的增加总是以灵活性的降低为代价的。长语境 LLM 无疑是一项伟大的技术进步，也是谷歌的骄傲。当然，在这方面，Gemini 目前要优于 Claude 和 GPT4。另一方面，将双子座与 RAG 进行比较就没有什么意义了。

A long-context LLM has its price in terms of both economics and latency. Surely in the future, the cost per token will decrease and the speed will also be higher. But a 1M token is less impressive than it seems, or at least for the real world. We produce a lot of data, and that data is very often unstructured. 1M tokens are 40MB, but every company has terabytes of data.
长上下文 LLM 在经济性和延迟方面都有其代价。当然，未来每个代币的成本会降低，速度也会提高。但 100 万个代币并没有想象中那么令人印象深刻，至少在现实世界中是这样。我们会产生大量数据，而这些数据往往是非结构化的。100 万个代币相当于 40MB，但每家公司都有 TB 级的数据。

Also, an LLM is limited both by the knowledge they learn during pretraining but also by general skills. New RAG paradigms with end-to-end fine-tuning aim instead to solve these problems. Especially for specialized domains, a small model with an RAG that undergoes adaptation to specific knowledge is better. Medicine, related fields, and finance are dynamic fields where yesterday’s knowledge is already obsolete. Therefore, there is a mismatch between the model’s prior knowledge and the new knowledge required to be effective. We can envision a future, where an LLM+RAG will often be fine-tuned for these domains. Or systems that conduct a continuous update and adapt to today’s web service.
此外，LLM受限于预培训期间所学的知识和一般技能。具有端到端微调功能的新 RAG 范式旨在解决这些问题。特别是对于专业领域来说，具有根据特定知识进行调整的 RAG 的小型模型效果更好。医学、相关领域和金融都是动态领域，昨天的知识已经过时。因此，模型的先验知识与有效所需的新知识之间存在不匹配。我们可以设想，在未来，LLM+RAG 将经常针对这些领域进行微调。或者是进行持续更新并适应当今网络服务的系统。

If it is true that the strength of LLM is reasoning, new paradigms of RAG are designed to strengthen these capabilities. New techniques will evolve in which both retrieval and COT will intersperse.
如果 LLM 的优势确实在于推理，那么新的 RAG 范例就是为了加强这些能力而设计的。新技术将不断发展，其中将穿插检索和 COT。

Finally, LLMs are black boxes, and the RAG enhances the transparency of the system. The RAG allows tracking of which knowledge and documents were used for generation. The EU AI Act is coming and will not be the only legislation directed at regulating LLMs. Whatever they are, legislators are geared toward accountability of these models and transparency of decisions. In such a future, RAG seems to be an essential component.
最后，LLMs 是黑盒子，而 RAG 增强了系统的透明度。通过 RAG，可以跟踪哪些知识和文件被用于生成。欧盟人工智能法案》即将出台，它不会是唯一一部旨在规范 LLMs 的立法。无论它们是什么，立法者都将致力于这些模型的问责制和决策的透明度。在这样的未来，RAG 似乎是必不可少的组成部分。

TL;DR 简要说明
The LLMs can hallucinate, thus producing responses that are incorrect or plain wrong. The RAG paradigm evolved to correct this behavior: an LLM is connected to external information and the extended context is provided to the model.
1001#会产生幻觉，从而产生不正确或完全错误的反应。RAG 范式就是为了纠正这种行为而发展起来的：LLM 与外部信息相连，并向模型提供扩展的上下文。
Some of the advantages of the RAG were increased privacy and retrieval of relevant information. Vector databases can be transformed back to the original documents, showing that databases are vulnerable. Second, the similarity function we use to retrieve documents has some limitations. Third, long-context LLMs are challenging RAG because the LLM can retrieve information in long documents without external components. These challenges are impacting the future of RAG.
RAG 的一些优势在于提高了隐私性和相关信息的检索。向量数据库可以被转换回原始文档，这表明数据库是脆弱的。其次，我们用来检索文档的相似性函数有一些局限性。第三，长上下文 LLMs 正在挑战 RAG，因为 LLM 可以检索长文档中的信息，而无需外部组件。这些挑战影响着 RAG 的未来。
Long-context LLM has a higher cost in both computational and speed. Moreover, Google’s claims aside, many researchers are skeptical that an LLM is really capable of using a long-context window. On the other hand, RAGs allow tracking of documents used for generation, can be connected to unstructured data, and are more functional for specialized domains. Therefore, even a long-context LLm itself would benefit from being connected to an RAG.
长上下文 LLM 的计算成本和速度成本都较高。此外，撇开谷歌的说法不谈，许多研究人员都怀疑 LLM 是否真的能够使用长语境窗口。另一方面，RAG 可以跟踪用于生成的文档，可以连接到非结构化数据，而且在专业领域的功能更强。因此，即使是长语境 LLm 本身也会从与 RAG 的连接中受益。
RAG is evolving for the new challenges of the future. Long-context LLM will enable new chunking and retrieval strategies. Similarly, KV caching and RAG will work in concert to reduce latency times. On the one hand we will have long-context LLMs and RAGs for generic applications, while small LLMs will be used with specialized RAG architectures for specialized domains.
RAG 正在不断发展，以应对未来的新挑战。长上下文 LLM 将支持新的分块和检索策略。同样，KV 缓存和 RAG 将协同工作，缩短延迟时间。一方面，我们将为通用应用提供长上下文 LLMs 和 RAG，另一方面，小型 LLMs 将与专门的 RAG 架构一起用于专门领域。