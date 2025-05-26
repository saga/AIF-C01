探索两种提高基础模型 （FM） 性能的技术：检索增强生成 （RAG） 和微调。您将了解帮助使用矢量数据库存储嵌入的 Amazon Web Services （AWS） 服务，以及代理在多步骤任务中的作用。您还将定义微调 FM 的方法，了解如何准备数据以进行微调等。


## title1

Embedding is the process by which text, images, and audio are given numerical representation in a vector space. Embedding is usually performed by a machine learning (ML) model. The following diagram provides more details about embedding. 
嵌入是在向量空间中为文本、图像和音频提供数字表示的过程。嵌入通常由机器学习 （ML） 模型执行。下图提供了有关嵌入的更多详细信息。

https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1748246400/ioosFlBVrQW10J9qBeI0Ag/tincan/914789_1717713712_o_1hvnrdq96oal1nua1bo61jun11ppb_zip/assets/vector%403x.png

Enterprise datasets, such as documents, images and audio, are passed to ML models as tokens and are vectorized. These vectors in an n-dimensional space, along with the metadata about them, are stored in purpose-built vector databases for faster retrieval.
企业数据集（如文档、图像和音频）作为令牌传递给 ML 模型，并进行矢量化。n 维空间中的这些向量以及有关它们的元数据存储在专门构建的向量数据库中，以便更快地检索。

Two words that relate to each other will have similar embeddings.
彼此相关的两个单词将具有相似的嵌入。

Here is an example of two words: sea and ocean. They are randomly initialized and their early embeddings are diverse. As the training progresses, their embeddings become more similar because they often appear close to each other and in similar context. For the purpose of this example, embeddings that are close together are represented by colors in the same palette. Therefore, the word sea and ocean use similar colors. However, stapler has a completely different embedding, so it uses a separate set of colors. 
下面是两个词的示例：sea 和 ocean。它们是随机初始化的，并且它们的早期嵌入是多种多样的。随着训练的进行，它们的嵌入变得更加相似，因为它们通常彼此靠近且在相似的上下文中出现。在此示例中，彼此靠近的嵌入由同一调色板中的颜色表示。因此，单词 sea 和 ocean 使用相似的颜色。但是，stapler 具有完全不同的嵌入，因此它使用一组单独的颜色。

Words that relate to each other will have closer embeddings.
彼此相关的单词将具有更紧密的嵌入。

### Storing vectors  存储向量

The core function of vector databases is to compactly store billions of high-dimensional vectors representing words and entities. Vector databases provide ultra-fast similarity searches across these billions of vectors in real time. 
向量数据库的核心功能是紧凑地存储数十亿个表示单词和实体的高维向量。矢量数据库可在这数十亿个矢量中实时提供超快速的相似性搜索。

The most common algorithms used to perform the similarity search are k-nearest neighbors (k-NN) or cosine similarity.
用于执行相似性搜索的最常见算法是 k 最近邻 （k-NN） 或余弦相似度。

Amazon Web Services (AWS) offers the following viable vector database options:
Amazon Web Services （AWS） 提供以下可行的矢量数据库选项：

- Amazon OpenSearch Service (provisioned) Amazon OpenSearch Service（预置）

- Amazon OpenSearch Serverless Amazon OpenSearch 无服务器

- pgvector extension in Amazon Relational Database Service (Amazon RDS) for PostgreSQL
适用于 PostgreSQL 的 Amazon Relational Database Service （Amazon RDS） 中的 pgvector 扩展

- pgvector extension in Amazon Aurora PostgreSQL-Compatible Edition
Amazon Aurora PostgreSQL 兼容版中的 pgvector 扩展

- Amazon Kendra  亚马逊肯德拉

## title1


## title1


## title1


## title1

***

## title1


