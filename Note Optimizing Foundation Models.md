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


## Fine-Tuning  微调

Although foundation models are highly versatile, they often require fine-tuning to tailor their broad capabilities to specific applications or to enhance their performance in particular domains. Fine-tuning is critical because it helps to do the following:
尽管基础模型用途广泛，但它们通常需要进行微调，以便为特定应用程序定制其广泛的功能，或增强它们在特定领域的性能。微调至关重要，因为它有助于执行以下作：

- Increase specificity: Adapt the model’s responses or predictions to the nuances of a specific domain or task that were not adequately covered in the initial training.
提高特异性：根据初始训练中未充分涵盖的特定领域或任务的细微差别调整模型的响应或预测。

- Improve accuracy: Enhance the model's performance on specialized tasks by training on domain-specific data, thereby reducing errors that occur due to the generic nature of foundational training.
提高准确性：通过对特定于领域的数据进行训练，提高模型在专业任务上的性能，从而减少由于基础训练的通用性质而发生的错误。

- Reduce biases: Address and mitigate any biases inherent in the initial training data, making the model more fair and appropriate for different applications.
减少偏差：解决并减轻初始训练数据中固有的任何偏差，使模型更加公平并适用于不同的应用程序。

- Boost efficiency: Streamline the model’s operations within specific contexts, potentially reducing computational requirements and speeding up response times.
提高效率：简化模型在特定上下文中的作，从而可能减少计算要求并加快响应时间。

### The different fine-tuning approaches
不同的微调方法

- Instruction tuning: This approach involves retraining the model on a new dataset that consists of prompts followed by the desired outputs. This is structured in a way that the model learns to follow specific instructions better. This method is particularly useful for improving the model's ability to understand and execute user commands accurately, making it highly effective for interactive applications like virtual assistants and chatbots. 
指令调整：此方法涉及在新数据集上重新训练模型，该数据集由提示和所需的输出组成。其结构方式使模型学会更好地遵循特定指令。这种方法对于提高模型准确理解和执行用户命令的能力特别有用，使其对于虚拟助手和聊天机器人等交互式应用程序非常有效。

- Reinforcement learning from human feedback (RLHF): This approach is a fine-tuning technique where the model is initially trained using supervised learning to predict human-like responses. Then, it is further refined through a reinforcement learning process, where a reward model built from human feedback guides the model toward generating more preferable outputs. This method is effective in aligning the model’s outputs with human values and preferences, thereby increasing its practical utility in sensitive applications.
来自人类反馈的强化学习 （RLHF）：这种方法是一种微调技术，其中模型最初使用监督学习进行训练，以预测类似人类的反应。然后，通过强化学习过程进一步完善它，其中根据人类反馈构建的奖励模型指导模型生成更可取的输出。这种方法可以有效地使模型的输出与人类价值观和偏好保持一致，从而提高其在敏感应用中的实际实用性。

https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1748246400/ioosFlBVrQW10J9qBeI0Ag/tincan/914789_1717713712_o_1hvnrdq96oal1nua1bo61jun11ppb_zip/assets/finetuning%403x.png

RLHF refers to the improvement of the model by learning from feedback, such as ratings, preferences, demonstrations, helpfulness, or toxicity, provided by humans. RLHF is used during the pretraining phase of the model but can also be used to fine-tune the model.
RLHF 是指通过从人类提供的反馈（例如评级、偏好、演示、帮助性或毒性）中学习来改进模型。RLHF 在模型的预训练阶段使用，但也可用于微调模型。

- Adapting models for specific domains: This approach involves fine-tuning the model on a corpus of text or data that is specific to a particular industry or sector.  An example of this would be legal documents for a legal AI or medical records for a healthcare AI. This specificity enables the model to perform with a higher degree of relevance and accuracy in domain-specific tasks, providing more useful and context-aware responses.
为特定领域调整模型：这种方法涉及在特定于特定行业或部门的文本或数据语料库上微调模型。这方面的一个例子是法律 AI 的法律文档或医疗保健 AI 的医疗记录。这种特异性使模型能够在特定于域的任务中以更高的相关性和准确性执行，从而提供更有用和上下文感知的响应。

- Transfer learning: This approach is a method where a model developed for one task is reused as the starting point for a model on a second task. For foundational models, this often means taking a model that has been trained on a vast, general dataset, then fine-tuning it on a smaller, specific dataset. This method is highly efficient in using learned features and knowledge from the general training phase and applying them to a narrower scope with less additional training required.
迁移学习：这种方法是为一项任务开发的模型作为第二个任务的模型的起点。对于基础模型，这通常意味着采用已在大型通用数据集上训练的模型，然后在较小的特定数据集上对其进行微调。这种方法可以非常有效地使用从一般训练阶段学到的特征和知识，并将它们应用于更狭窄的范围，所需的额外培训更少。

- Continuous pretraining: This approach involves extending the training phase of a pre-trained model by continuously feeding it new and emerging data. This approach is used to keep the model updated with the latest information, vocabulary, trends, or research findings, ensuring its outputs remain relevant and accurate over time. 
持续预训练：这种方法涉及通过不断向预训练模型提供新的和新兴的数据来扩展预训练模型的训练阶段。这种方法用于使模型保持最新信息、词汇、趋势或研究结果的更新，确保其输出随着时间的推移保持相关性和准确性。


### Preparing the data for the fine-tuning step
为微调步骤准备数据

During the initial training phase, a foundational model is trained on a vast and diverse dataset. This dataset typically encompasses a wide range of topics to develop a broad understanding and general capabilities. The goals during this phase are as follows:
在初始训练阶段，基础模型在庞大而多样化的数据集上进行训练。此数据集通常包含广泛的主题，以发展广泛的理解和一般能力。此阶段的目标如下：

- Extensive coverage: Ensuring the dataset covers a broad spectrum of knowledge to give the model a robust foundational understanding
覆盖范围广：确保数据集涵盖广泛的知识范围，为模型提供可靠的基础理解

- Diversity: Including varied types of data from numerous sources to equip the model with the ability to handle a wide array of tasks
多样性：包括来自众多来源的各种类型的数据，使模型能够处理各种任务

- Generalization: Focusing on building a model that can generalize across different tasks and domains without specific tailoring
泛化：专注于构建一个可以跨不同任务和领域泛化的模型，而无需进行特定定制

Data preparation for this phase involves collecting as much data as possible. The data is often from publicly available sources, curated datasets, and sometimes proprietary data, depending on the model's intended usage. The data needs thorough cleaning and possibly anonymization to ensure privacy and compliance with regulations.
此阶段的数据准备涉及收集尽可能多的数据。数据通常来自公开可用的来源、精选数据集，有时还来自专有数据，具体取决于模型的预期用途。数据需要彻底清理，并可能进行匿名化处理，以确保隐私并遵守法规。

### Data preparation for fine-tuning
用于微调的数据准备

Fine-tuning, on the other hand, is a more targeted process where a pretrained model is adapted to perform well on a specific task or within a particular domain. The data preparation for fine-tuning is distinct from initial training due to the following reasons:
另一方面，微调是一个更具针对性的过程，其中预训练模型经过调整，以便在特定任务或特定领域内表现良好。由于以下原因，用于微调的数据准备与初始训练不同：

- Specificity: The dataset for fine-tuning is much more focused, containing examples that are directly relevant to the specific tasks or problems the model needs to solve.
特异性：用于微调的数据集更加集中，包含与模型需要解决的特定任务或问题直接相关的示例。

- High relevance: Data must be highly relevant to the desired outputs. Examples include legal documents for a legal AI or customer service interactions for a customer support AI.
高相关性：数据必须与所需的输出高度相关。示例包括法律 AI 的法律文档或客户支持 AI 的客户服务交互。

- Quality over quantity: Although the initial training requires massive amounts of data, fine-tuning can often achieve significant improvements with much smaller, but well-curated datasets.
质量胜于数量：尽管初始训练需要大量数据，但微调通常可以使用更小但精心策划的数据集实现显著改进。


### Key steps in fine-tuning data preparation
微调数据准备的关键步骤

The following list walks through the key steps in fine-tuning data preparation:
以下列表介绍了微调数据准备的关键步骤：

1. Data curation: Although it is a continuation, this involves a more rigorous selection process to ensure every piece of data is highly relevant. This step also ensures the data contributes to the model's learning in the specific context.
数据管理：虽然这是一个延续，但这涉及更严格的选择过程，以确保每条数据都高度相关。此步骤还确保数据有助于模型在特定上下文中的学习。

2. Labeling: In fine-tuning, the accuracy and relevance of labels are paramount. They guide the model's adjustments to specialize in the target domain.
标签：在微调中，标签的准确性和相关性至关重要。它们指导模型的调整以专注于目标域。

3. Governance and compliance: Considering fine-tuning often uses more specialized data, ensuring data governance and compliance with industry-specific regulations is critical.
治理和合规性：考虑到微调通常会使用更专业的数据，因此确保数据治理和遵守行业特定法规至关重要。

4. Representativeness and bias checking: It is essential to ensure that the fine-tuning dataset does not introduce or perpetuate biases that could skew the model's performance in undesirable ways.
代表性和偏差检查：必须确保微调数据集不会引入或延续可能以不良方式扭曲模型性能的偏差。

5. Feedback integration: For methods like RLHF, incorporating user or expert feedback directly into the training process is crucial. This is more nuanced and interactive than the initial training phase.
反馈集成：对于 RLHF 等方法，将用户或专家反馈直接纳入培训过程至关重要。这比初始培训阶段更加细致和互动。


## Model evaluation  模型评估

When evaluating the performance of language models, especially those involved in generating or transforming text, specific metrics can be used. These metrics are made to assess the quality of the output, compared to a human-written standard. Three commonly used metrics for this purpose are Recall-Oriented Understudy for Gisting Evaluation (ROUGE), Bilingual Evaluation Understudy (BLEU), and BERTScore.
在评估语言模型的性能时，尤其是那些涉及生成或转换文本的语言模型，可以使用特定的指标。与人工编写的标准相比，这些指标用于评估输出的质量。用于此目的的三个常用指标是面向召回的 **Gisting 评估 （ROUGE）、双语评估 Understudy （BLEU） 和 BERTScore**。

### ROUGE  

ROUGE is a set of metrics used to evaluate automatic summarization of texts, in addition to machine translation quality in NLP. The main idea behind ROUGE is to count the number of overlapping units. This includes words, N-grams, or sentence fragments between the computer-generated output and a set of reference (human-created) texts.
**ROUGE 是一组指标，用于评估文本的自动摘要，以及 NLP 中的机器翻译质量**。ROUGE 背后的主要思想是计算重叠单元的数量。这包括计算机生成的输出和一组参考（人工创建）文本之间的单词、N 元语法或句子片段。

The following are two ways to use the ROUGE metric:
以下是使用 ROUGE 度量的两种方法：

- ROUGE-N: This metric measures the overlap of n-grams between the generated text and the reference text. For example, ROUGE-1 refers to the overlap of unigrams, ROUGE-2 refers to bigrams, and so on. This metric primarily assesses the fluency of the text and the extent to which it includes key ideas from the reference.
ROUGE-N：此指标衡量生成的文本和参考文本之间的 n-gram 重叠。例如，ROUGE-1 表示一元语法的重叠，ROUGE-2 表示二元语法，依此类推。该指标主要评估文本的流畅性以及它包含参考文献中关键思想的程度。

- ROUGE-L: This metric uses the longest common subsequence between the generated text and the reference texts. It is particularly good at evaluating the coherence and order of the narrative in the outputs.
ROUGE-L：此指标使用生成的文本和参考文本之间最长的公共子序列。它特别擅长评估输出中叙述的连贯性和顺序。

ROUGE is widely used because it is not complex. It is interpretable, and correlates reasonably well with human judgment, especially when evaluating the recall aspect of summaries. The evaluations assess how much of the important information in the source texts is captured by the generated summaries.
ROUGE 被广泛使用，因为它并不复杂。它是可解释的，并且与人类判断有相当好的相关性，尤其是在评估摘要的回忆方面时。评估评估生成的摘要捕获了源文本中多少重要信息。


### BLEU  

BLEU is a metric used to evaluate the quality of text that has been machine-translated from one natural language to another. Quality is calculated by comparing the machine-generated text to one or more high-quality human translations. BLEU measures the precision of N-grams in the machine-generated text that appears in the reference texts and applies a penalty for overly short translations (brevity penalty).
**BLEU 是用于评估已从一种自然语言机器翻译为另一种自然语言的文本质量的指标**。质量的计算方法是将机器生成的文本与一个或多个高质量的人工翻译进行比较。BLEU 测量参考文本中出现的机器生成文本中 N 元语法的精度，并对过短的翻译进行惩罚（简洁惩罚）。

Unlike ROUGE, which focuses on recall, BLEU is fundamentally a precision metric. It checks how many words or phrases in the machine translation appear in the reference translations. BLEU evaluates the quality at the level of the sentence, typically using a combination of unigrams, bigrams, trigrams, and quadrigrams. A brevity penalty discourages overly concise translations that might influence the precision score.
与专注于召回率的 ROUGE 不同，BLEU 从根本上说是一个精确指标。它检查机器翻译中有多少单词或短语出现在参考翻译中。BLEU 在句子级别评估质量，通常使用 unigrams、bigrams、trigrams 和 quadrigrams 的组合。简洁性惩罚会阻止可能影响精确率分数的过于简洁的翻译。

BLEU is popular in the field of machine translation for its ease of use and effectiveness at a broad scale. However, it has limitations in assessing the fluency and grammaticality of the output.
BLEU 因其易用性和广泛的有效性而在机器翻译领域广受欢迎。但是，它在评估输出的流畅性和语法性方面存在局限性。

### The BERTScore

BERTScore uses the pretrained contextual embeddings from models like BERT to evaluate the quality of text-generation tasks. BERTScore computes the cosine similarity between the contextual embeddings of words in the candidate and the reference texts. This is unlike traditional metrics that rely on exact matches of N-grams or words.
BERTScore 使用来自 BERT 等模型的预训练上下文嵌入来评估文本生成任务的质量。BERTScore 计算候选文本和参考文本中单词的上下文嵌入之间的余弦相似度。这与依赖于 N-gram 或单词的精确匹配的传统指标不同。

Because BERTScore evaluates the semantic similarity rather than relying on exact lexical matches, it is capable of capturing meaning in a more nuanced manner. BERTScore is less prone to some of the pitfalls of BLEU and ROUGE. An example of this is their sensitivity to minor paraphrasing or synonym usage that does not affect the overall meaning conveyed by the text.
由于 **BERTScore 评估语义相似性而不是依赖于精确的词汇匹配**，因此它能够以更细致的方式捕获含义。BERTScore 不太容易受到 BLEU 和 ROUGE 的一些陷阱的影响。这方面的一个例子是他们对不影响文本传达的整体含义的次要释义或同义词使用的敏感性。

BERTScore is increasingly used alongside traditional metrics like BLEU and ROUGE for a more comprehensive assessment of language generation models. This is especially true in cases where capturing the deeper semantic meaning of the text is important.
BERTScore 越来越多地与 BLEU 和 ROUGE 等传统指标一起使用，以更全面地评估语言生成模型。在捕获文本的更深层次语义很重要的情况下尤其如此。

https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1748246400/ioosFlBVrQW10J9qBeI0Ag/tincan/914789_1717713712_o_1hvnrdq96oal1nua1bo61jun11ppb_zip/assets/modeleval2%403x.png


### Quiz

You are evaluating the performance of a language generation model on various text generation tasks, such as machine translation, summarization, and open-ended text generation. To assess the quality of the generated text, you need to choose an appropriate evaluation metric that can capture the semantic similarity between the model's output and human-generated reference texts.
您正在评估语言生成模型在各种文本生成任务 （如机器翻译、摘要和开放式文本生成） 上的性能。要评估生成文本的质量，您需要选择一个适当的评估指标，该指标可以捕获模型输出与人工生成的参考文本之间的语义相似性。

Based on the information provided, which evaluation metric would be the most suitable for this scenario?
根据提供的信息，哪种评估指标最适合此方案？

**BERTScore**

## title1


## title1


***

## title1


