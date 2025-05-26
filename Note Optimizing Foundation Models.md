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

## Key functions of agents  代理的主要功能

Agents can serve different roles in a generative AI application, such as the following:
代理可以在生成式 AI 应用程序中担任不同的角色，例如：

- Intermediary operations: Agents can act as intermediaries, facilitating communication between the generative AI model and various backend systems. The generative AI model handles language understanding and response generation. The various backend systems include items such as databases, CRM platforms, or service management tools.
中介作：代理可以充当中介，促进生成式 AI 模型与各种后端系统之间的通信。生成式 AI 模型处理语言理解和响应生成。各种后端系统包括数据库、CRM 平台或服务管理工具等项目。

- Actions launch: Agents can be used to run a wide variety of tasks. These tasks might include adjusting service settings, processing transactions, retrieving documents, and more. These actions are based on the users' specific needs understood by the generative AI model.
作启动：代理可用于运行各种任务。这些任务可能包括调整服务设置、处理交易、检索文档等。这些作基于生成式 AI 模型所理解的用户特定需求。

- Feedback integration: Agents can also contribute to the AI system's learning process by collecting data on the outcomes of their actions. This feedback helps refine the AI model, enhancing its accuracy and effectiveness in future interactions.
反馈集成：代理还可以通过收集有关其作结果的数据来为 AI 系统的学习过程做出贡献。此反馈有助于改进 AI 模型，提高其在未来交互中的准确性和有效性。

https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1748246400/ioosFlBVrQW10J9qBeI0Ag/tincan/914789_1717713712_o_1hvnrdq96oal1nua1bo61jun11ppb_zip/assets/agentsdiagram%403x.png



## Evaluate results  评估结果

Evaluating the performance of generative AI models is critical for understanding their effectiveness and ensuring they meet indented objectives. Two of the most common evaluation methods are human evaluation and the use of benchmark datasets. Each method provides unique insights and is suitable for different aspects of model performance assessment.
评估生成式 AI 模型的性能对于了解其有效性并确保它们满足缩进目标至关重要。两种最常见的评估方法是人工评估和使用基准数据集。每种方法都提供了独特的见解，适用于模型性能评估的不同方面。


### Human evaluation  人工评估

Human evaluation involves real users interacting with the AI model to provide feedback based on their experience. This method is particularly valuable for assessing qualitative aspects of the model, such as the following:
人工评估涉及真实用户与 AI 模型交互，以根据他们的体验提供反馈。此方法对于评估模型的定性方面特别有价值，例如：

- User experience: How intuitive and satisfying is the interaction with the model from the user's perspective?
用户体验：从用户的角度来看，与模型的交互有多直观和令人满意？

- Contextual approriateness: Does the model respond in a way that is contextually relevant and sensitive to the nuances of human communication?
情境适应性：模型是否以一种与情境相关且对人类交流的细微差别敏感的方式做出回应？

- Creativity and flexibility: How well does the model handle unexpected queries or complex scenarios that require a nuanced understanding?
创造力和灵活性：模型处理需要细致入微理解的意外查询或复杂场景的能力如何？

### Benchmark datasets  对数据集进行基准测试

Benchmark datasets, on the other hand, provide a quantitative way to evaluate generative AI models. These datasets consist of predefined datasets and associated metrics that offer a consistent, objective means to measure model performances. This might include the following:
另一方面，基准测试数据集提供了一种评估生成式 AI 模型的定量方法。这些数据集由预定义的数据集和相关指标组成，这些指标为衡量模型性能提供了一致、客观的方法。这可能包括以下内容：

- Accuracy: How accurately does the model perform specific tasks according to predefined standards?
准确性：模型根据预定义标准执行特定任务的准确度如何？

- Speed and efficiency: How quickly does the mode generate responses and how does this impact operational efficiency?
速度和效率：该模式生成响应的速度有多快，这对运营效率有何影响？

- Scalability: Can the mode maintain its performance as the scale of data or number of users increases?
可扩展性：随着数据规模或用户数量的增加，该模式能否保持其性能？

Benchmark datasets are particularly useful for initial testing phases to ensure that the model meets certain technical specifications before it is put through more subjective human evaluations. They are also essential for comparing performance across different models or different iterations of the same model.
基准测试数据集对于初始测试阶段特别有用，以确保模型在经过更主观的人工评估之前满足某些技术规范。它们对于比较不同模型或同一模型的不同迭代的性能也是必不可少的。

### Combined approach  组合方法

In practice, a combination of both human evaluation and benchmark datasets is often used to provide a comprehensive overview of a model's performance. Although benchmark datasets can quantify the model's technical capabilities, human evaluation brings an essential human-centric perspective that benchmarks cannot capture alone. This combined approach ensures that the model is not only technically proficient but also effective and engaging in real-world scenarios.
在实践中，通常使用人工评估和基准数据集的组合来提供模型性能的全面概述。尽管基准数据集可以量化模型的技术能力，但人工评估带来了一个重要的以人为本的视角，而基准无法单独捕捉到这一点。这种组合方法确保模型不仅技术熟练，而且有效且参与实际场景。




## title1

***

## title1


