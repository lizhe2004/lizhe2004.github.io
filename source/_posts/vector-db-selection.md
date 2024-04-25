# 您应该使用哪个向量数据库？选择最适合您需求的一款

## 介绍

向量数据库已成为存储和索引非结构化和结构化数据表示（representation）的首选。这些表示称为向量嵌入（vector embedding），是由嵌入模型生成的。向量存储在那些利用深度学习模型（尤其是大型语言模型）的应用开发中发挥着至关重要的作用。

## 什么是向量数据库？

在现实世界中，并非所有数据都可以整齐地放到行和列中。在处理图像、视频和自然语言等复杂的非结构化数据时尤其如此。这就是向量数据库的用武之地。

 向量数据库是一种以高维向量的形式来存储数据的数据库，这些向量本质上是表示一个对象的特征或特性的数字列表或者叫数组。每个向量对应一个唯一的实体，例如一段文本、一张图像或一段视频。

但为什么要使用向量呢？神奇之处在于它们捕捉语义和相似性的能力。通过将数据表示为向量，我们可以在数学计算的层面比较它们并确定它们的相似或不不相似的程度。这使我们能够执行复杂的查询，例如“找到与这张图相似的图片”或“检索与此文本语义相关的文档”。

## 为什么需要向量数据库？

近年来，向量数据库变得越来越流行，特别是在机器学习（ML）和人工智能（AI）领域。人工智能和机器学习模型的复杂性需要有效的方法来存储、搜索和检索它们处理的大量非结构化数据。

对于为结构化数据构建的传统数据库来说，向量数据的复杂性和大小通常可能太大。相反，向量数据库就是专门为此而设计的。他们提供专门的搜索和索引算法，即使在拥有数十亿条目的数据库中，也可以快速找到可比较的向量。

也有一些声音是“向量存储检索是个真需求，然而专用向量数据库已经凉了。”。因为现在一些传统数据库也都开始通过向量插件的形式来支持了向量存储和检索。比如postgresql可以通过开源向量检索插件PG Vector实现，redis 和elasticsearch的最新版本也都开始支持向量检索。关于这方面的讨论还没有结束，专用向量数据库和增加了向量检索功能的传统数据库各自有自己的优缺点以及适合的场景，本文就不再展开讨论。至少有一点大家是一致的，“向量存储和检索的需求是存在的，本文重点放在专用向量数据库方面。

## 向量数据库的不同使用场景

人工智能和机器学习的应用借助于向量查找的能力而得到极大扩展。典型使用场景包括以下内容：

RAG系统：向量数据库可以与大型语言模型（LLM）结合在一起，构建以知识为基础的以自然语言为输入的智能应用。
推荐系统：高度个性化的推荐引擎可以由向量数据库提供支持，向量数据库将用户偏好和项目属性表示为向量。

向量数据库通过搜索视觉相关的图像或视频，彻底改变了基于内容的检索。

自然语言处理：向量数据库通过将文本转换为向量来提供语义搜索、主题建模和文档分类或聚集。
欺诈检测：为了识别金融交易中的趋势和异常情况，也会使用到向量数据库。

## 向量数据库对比

向量数据库有很多 - 例如 Qdrant、Pinecone、Milvus、Chroma、Weaviate 等。每个数据库都有自己的优势、权衡和理想的使用场景。在这里，我们将深入研究一些流行的向量数据库并进行全面比较，包括 Pinecone、Milvus、Chroma、Weaviate、Faiss、Elasticsearch 和 Qdrant。

## 部署方案

Pinecone在这方面是个特殊的存在。由于出于性能和可扩展性原因，Pinecone 是一项完全托管的服务，因此我们无法在本地运行数据库实例。 Milvus、Chroma、Weaviate、Faiss、Elasticsearch 和 Qdrant 都可以在本地部署运行；而且大多数都提供了Docker镜像来简化操作。

| 向量数据库 | 本地部署 | 云部署| 私有部署|
|---|---|---|---|
|   Qdrant | 支持 | 自托管 | 支持 |
|   Pinecone | 不支持 | 托管 | 支持 |
|   Milvus | 支持 | 自托管 | 支持 |
|   Chroma | 支持 | 自托管 | 支持 |
|   Weaviate | 支持 | 自托管 | 支持 |
|   Faiss | 支持 | 不支持 | 支持 |
|   Elasticsearch | 支持 | 自托管 | 支持 |

## 可扩展性

Qdrant 提供静态分片；如果数据增长超出了服务器的容量，需要向集群添加更多机器并重新分片所有数据。这可能是一个耗时且复杂的过程。此外，不平衡的分片可能会导致系统瓶颈并降低系统的效率。

Pinecone 通过其Serveless层支持计算和存储的分离。对于基于 POD 的集群，Pinecone 采用静态分片，这需要用户在扩展集群时手动对数据重新分片。

Weaviate 提供静态分片。如果Chroma不能在多个节点之间分配和管理数据，那么它就无法扩展到多个节点。

| 向量数据库 | 水平扩展 | 垂直扩展| 分布式架构|
|---|---|---|---|
|   Qdrant | 支持 | 支持 | 支持 |
|   Pinecone | 支持 | 支持 | 支持 |
|   Milvus | 支持 | 支持 | 支持 |
| Chroma | 支持 | 支持 | 支持 |
|   Weaviate | 支持 | 支持 | 支持 |
|  Faiss | 不支持 | 支持 | 不支持 |
|   Elasticsearch | 支持 | 支持 | 支持 |

## 性能基准测试

无论我们选择的精度阈值和指标如何，Qdrant 在几乎所有场景中都能实现最高的 RPS 和最低的延迟。它还显示其中一个数据集的 RPS 提高了 4 倍。

对于许多使用场景来说，Elasticsearch 已经变得相当快，但在索引时间方面却非常慢。当存储 10M+ 96 维向量时，速度可能会慢 10 倍！ （32 分钟 vs 5.5 小时）
Milvus is the fastest when it comes to indexing time and maintains good precision. However, it’s not on-par with the others when it comes to RPS or latency, when you have higher dimension embeddings or more numbers of vectors.
Milvus 的索引时间是最快的，并且保持了良好的精度。然而，当您拥有更高维度的嵌入或更多数量的向量时，在 RPS 或延迟方面，它与其他数据库并不相当。
Redis is able to achieve good RPS but mostly for lower precision. It also achieved low latency with a single thread; however its latency goes up quickly with more parallel requests. Part of this speed gain comes from its custom protocol.
Redis 能够实现良好的 RPS，但主要是精度较低。它还通过单线程实现了低延迟；然而，随着并行请求的增加，其延迟会迅速增加。这种速度增益部分来自其自定义协议。
Weaviate has improved the least over time. Because of relative improvements in other engines, it has become one of the slowest in terms of RPS as well as latency.
随着时间的推移，Weaviate 的改进最少。由于其他引擎的相对改进，它已成为 RPS 和延迟方面最慢的引擎之一。
| 向量数据库 | 设置 | 数据集| 上传时间（m）|上传时间+索引时间|P95(ms)|RPS|P99(ms)|延迟|精确度（Precision）|
|---|---|---|---|---|---|---|---|---|---|
|qdrant|qdrant-sq-rps-m-64-ef-512|dbpedia-openai-1M-1536-angular|3.51|24.43|4.95|1238|8.62|3.54|0.99|
|elasticsearch|elasticsearch-m-32-ef-128|dbpedia-openai-1M-1536-angular|19.18|83.72|72.53|716.8|135.68|22.1|0.98|
|redis|redis-m-32-ef-256|dbpedia-openai-1M-1536-angular|92.49|92.49|160.85|625.27|167.35|140.65|0.97|
|weaviate|weaviate-m-32-ef-256|dbpedia-openai-1M-1536-angular|25.98|25.98|465.42|352.5|782.39|279.44|0.97|
|milvus|milvus-m-16-ef-128|dbpedia-openai-1M-1536-angular|0.27|1.16|441.32|219.11|576.65|393.31|0.99|

## 数据管理

| 向量数据库 | 数据导入 | 数据更新| 数据备份和恢复|
|---|---|---|---|
|   Qdrant | 支持 | 支持 | 支持 |
|   Pinecone | 支持 | 支持 | 支持 |
| Milvus | 支持 | 支持 | 支持 |
| Chroma | 支持 | 支持 | 支持 |
|   Weaviate | 支持 | 支持 | 支持 |
|  Faiss | 支持 | 支持 | 不支持 |
|   Elasticsearch | 支持 | 支持 | 支持 |

## 向量相似度搜索

向量数据库如此有用的原因之一是它们可以告诉我们事物之间的关系以及它们的相似或不同程度。有多种距离度量可以让向量数据库做到这一点，并且不同的向量数据库实现了不同的距离度量。

| 向量数据库 | 距离指标（Distance Metrics） | ANN算法 | 过滤（Filtering）|后处理|
|---|---|---|---|---|
|   Qdrant | Cosine, Dot Product,L2 | HNSW | 支持 | 支持 |
| Pinecone | Cosine, Euclidean,  Dot Product | Proprietary(Pinecone Graph Algorithm) | 支持 | 支持 |
| MiLVus |Euclidean, Cosine,IP,L2,Harmming,Jacard,Tanimoto | HNSW,IVF_FLAT,IVF_SQ8,IVF_PQ,RNSG,ANNOY | 支持 | 支持 |
| Chroma | Cosine, Euclidean,Dot Product,L2 | HNSW | 支持 | 支持 |
| Weaviate | Cosine,  | HNSW | 支持 | 支持 |
| Faiss | L2,Cosine, IP, L1,Linf | IVF,HNSW,IMI,PQ | 支持 | 不支持 |
| Elasticsearch | Cosine, Dot Product, L1,L2 | HNSW | 支持| 支持 |

用更准确的说法应该叫{% katex %}||L||_1{% endkatex %}, {% katex %}||L||_2{% endkatex %} ,{% katex %}||L||_{\infty}​{% endkatex %}，即数值分析中的1-范数、2-范数、无穷范数。接下来为了方便描述起见仅以二维空间下的两点A(x<sub>1</sub>,y<sub>1</sub>)B(x<sub>2</sub>,y<sub>2</sub>)为例。

L1距离
即曼哈顿距离，可以简单理解为只能横着走或竖着走：

{% katex %}
d_1=|x_1-x_2|+|y_1-y_2|
{% endkatex %}

L2距离
即欧氏距离，也是我们平时最常用的，两点之间的直线距离：
{% katex %}
d_2 = \sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2}
{% endkatex %}

L-Inf距离
即切比雪夫距离，可以理解为国际象棋中国王的走子法，有八个方向可以移动：
{% katex %}
d_\infty = \max(|x_1 - x_2|, |y_1 - y_2|)
{% endkatex %}

## 集成和API

虽然 REST API 更常见，但 GRPC API 更关注于时延要求特别低的场景或需要快速移动大量数据时的性能和吞吐量。根据您的要求和网络，GRPC 可能比 REST 快几倍。

## 社区与生态系统

开源意味着我们可以浏览核心数据库的源代码，并且向量数据库具有灵活的许可模式。

## 价格
| 向量数据库 | 免费层 | 按需付费 | 企业方案|
|---|---|---|---|
| Qdrant| 支持| 不支持| 支持|
|Pinecone| 支持| 支持| 支持|
|Milvus| 支持| 不支持| 不支持|
|Chroma| 支持| 不支持| 不支持|
|Weaviate| 支持| 不支持| 支持|
|Faiss| 支持| 不支持| 不支持|
|Elasticsearch| 支持| 支持| 支持|

## 元数据过滤

元数据是一个非常强大的概念，与核心向量数据库功能相辅相成；它是模糊的人类语言和结构化数据之间的联系。这是该架构的基础，在该架构中，人类用户询问产品，人工智能购物助理会立即回复他们所描述的商品。
| 向量数据库 | 元数据支持 | 批处理 |监控和日志|
|---|---|---|---|
| Qdrant | 支持 | 支持 | 支持 |
| Pinecone | 支持 | 支持 | 支持 |
| Milvus | 支持 | 支持 | 支持 |
| Chroma | 支持 | 支持 | 不支持 |
| Weaviate | 支持 | 支持 | 支持 |
| Faiss | 不支持 | 支持 | 不支持 |
| Elasticsearch | 支持 | 支持 | 支持 |

## 向量数据库功能

Qdrant：Qdrant 使用三种类型的索引来支持其数据库。这三个索引是Payload索引，类似于传统的面向文档的数据库中的索引；字符串有效负载的全文索引,以及一个向量索引。他们的混合搜索方法是向量搜索与属性过滤的组合。
Pinecone：RBAC 对于大型组织来说还不够。存储优化 (S1) 存在一些性能问题，只能获得 10-50 QPS。命名空间的数量是有限的，用户在使用元数据过滤作为解决此限制的方法时应小心，因为它会对性能产生很大影响。此外，这种方法无法实现数据隔离。
Weaviate：Weaviate 使用两种类型的索引来支持其数据库。倒排索引将数据对象属性映射到其在数据库中的位置，向量索引支持高性能查询。此外，其混合搜索方法使用密集向量来理解查询的上下文，并将其与稀疏向量相结合以进行关键字匹配。
Chroma：Chroma使用HNSW算法支持kNN搜索。

Milvus：Milvus 支持多个内存索引和表级分区，从而满足实时信息检索系统所需的高性能。 RBAC 支持是企业级应用程序的要求。关于分区，通过将搜索限制为数据库的一个或多个子集，与静态分片相比，分区可以提供一种更有效的数据过滤方式，静态分片可能会引入瓶颈，并且当数据增长超出服务器容量时需要重新分片。分区是一种管理数据的好方法，它可以根据类别或时间范围将数据分组为子集。这可以帮助您轻松过滤和搜索大量数据，而不必每次都搜索整个数据库。没有一种索引类型可以适合所有用例，因为每个应用场景都会有不同的权衡。通过支持更多索引类型，您可以更灵活地在准确性、性能和成本之间找到平衡。
Faiss：FAISS是一种支持kNN搜索的算法

## 整体对比总结
![](https://cdn.jsdelivr.net/gh/lizhe2004/pic-repo@master/imgs/20240425165039.png)

## 为什么我选择Qdrant

Qdrant 提供了一套用 Rust 构建的生产可用的服务，这种语言以其安全性而闻名。 Qdrant 配备了一个用户友好的 API，旨在存储、搜索和管理高维点（点只不过是向量嵌入），并通过称为有效负载（payloads）的元数据进行加强。这些payloads成为有价值的信息，提高搜索精度并为用户提供有洞察力的数据。如果您熟悉 Chroma 等其他向量数据库，则 Payload 类似于元数据；它包含有关向量的信息。

使用 Rust 编写使得 Qdrant 成为即使在高负载下也能快速响应的可靠向量存储。 Qdrant 与其他数据库的区别在于它提供的客户端 API 数量。目前 Qdrant 支持 Python、TypeSciprt/JavaScript、Rust 和 Go。它使用 HSNW（Hierarchical Navigable Small World Graph）进行向量索引，并附带许多距离度量，如余弦、点和欧几里德。它附带了一个开箱即用的推荐 API。

考虑 Qdrant 时的一些关键要点包括：

Qdrant 采用 Rust 制作，即使在高负载下也能确保速度和可靠性，使其成为高性能向量存储的最佳选择。
Qdrant 的与众不同之处在于它对客户端 API 的支持，满足 Python、TypeScript/JavaScript、Rust 和 Go 开发人员的需求。
Qdrant 利用 HSNW 算法并提供不同的距离度量，包括 Dot、Cosine 和 Euclidean，使开发人员能够选择与其特定用例相符的度量。
Qdrant 通过可扩展的云服务无缝过渡到云，提供免费套餐选项用于试用尝试。无论数据量如何，其云原生架构都能确保最佳性能。

## Qdrant的优势

高效的相似搜索——Qdrant专为相似搜索操作而设计。它对于在大量数据中查找相似的嵌入非常快速且准确。
可扩展性——Qdrant 具有可扩展性，因为它可以有效地处理大量向量。
易于使用 — Qdrant 数据库提供了用户友好的 API，可以轻松设置、插入数据和执行类似的搜索。
开源 — Qdrant 是一个开源项目，这意味着我们可以访问源代码并为其开发做出贡献。
灵活性——Qdrant数据库支持灵活的schema，这意味着我们可以定义不同类型的向量字段，还可以存储和搜索不同类型的数据，例如图像、文本、音频等。

## 结论

Qdrant 是一个强大的工具，可以帮助企业释放语义嵌入的力量并彻底改变文本搜索。它为管理高维数据提供了可靠且可扩展的解决方案，具有出色的查询性能和易于集成的特点。其开源数据库允许持续开发、修复错误并进行改进。

Qdrant 提供灵活的部署选项（自托管或云管理）、高性能、向量维度无硬性限制、元数据过滤、混合搜索功能以及免费的自托管版本。