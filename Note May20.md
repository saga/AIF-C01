提示的形式取决于您为模型分配的任务。在浏览提示工程示例时，您将查看包含以下部分或全部元素的提示：

•Instructions: This is a task for the large language model to do. It provides a task description or instruction for how the model should perform.
说明：这是大型语言模型要执行的任务。它提供模型应如何执行的任务描述或说明。

•Context: This is external information to guide the model.
上下文：这是指导模型的外部信息。

•Input data: This is the input for which you want a response.
Input data：这是您希望响应的 Input。

•Output indicator: This is the output type or format.
输出指示器：这是输出类型或格式。


Temperature 温度： This parameter controls the randomness or creativity of the model's output. A higher temperature makes the output more diverse and unpredictable, and a lower temperature makes it more focused and predictable. Temperature is set between 0 and 1. The following are examples of different temperature settings.
此参数控制模型输出的随机性或创造性。较高的温度使输出更加多样化和不可预测，而较低的温度使其更加集中和可预测。温度设置在 0 到 1 之间。以下是不同温度设置的示例。

Top p is a setting that controls the diversity of the text by limiting the number of words that the model can choose from based on their probabilities. Top p is also set on a scale from 0 to 1. The following are examples of different top p settings.
Top p 是一种设置，它通过限制模型可以根据概率选择的单词数来控制文本的多样性。Top p 也设置为 0 到 1 之间的范围。以下是不同前 p 设置的示例。

Top k limits the number of words to the top k most probable words, regardless of their percent probabilities. For instance, if top k is set to 50, the model will only consider the 50 most likely words for the next word in the sequence, even if those 50 words only make up a small portion of the total probability distribution.
Top k 将单词数限制为前 k 个最可能的单词，而不管其概率百分比如何。例如，如果前 k 个单词设置为 50，则模型将只考虑序列中下一个单词最可能的 50 个单词，即使这 50 个单词只占总概率分布的一小部分。

The maximum length setting determines the maximum number of tokens that the model can generate during the inference process. This parameter helps to prevent the model from generating excessive or infinite output, which could lead to resource exhaustion or undesirable behavior. The appropriate value for this setting depends on the specific task and the desired output length. For instance, in natural language generation tasks like text summarization or translation, the maximum length can be set based on the typical length of the target text. In open-ended generation tasks, such as creative writing or dialogue systems, a higher maximum length might be desirable to allow for more extended outputs.
最大长度设置确定模型在推理过程中可以生成的最大令牌数。此参数有助于防止模型生成过多或无限的输出，这可能会导致资源耗尽或不良行为。此设置的适当值取决于特定任务和所需的输出长度。例如，在文本摘要或翻译等自然语言生成任务中，可以根据目标文本的典型长度设置最大长度。在开放式生成任务中，例如创意写作或对话系统，可能需要更高的最大长度，以允许更多的扩展输出。

Stop sequences are special tokens or sequences of tokens that signal the model to stop generating further output. When the model encounters a stop sequence during the inference process, it will terminate the generation regardless of the maximum length setting. Stop sequences are particularly useful in tasks where the desired output length is variable or difficult to predict in advance. For example, in conversational artificial intelligence (AI) systems, the stop sequence could be an end-of-conversation token or a specific phrase that indicates the end of the response.
停止序列是向模型发出信号以停止生成进一步输出的特殊标记或标记序列。当模型在推理过程中遇到停止序列时，无论最大长度设置如何，它都将终止生成。停止序列在所需输出长度可变或难以提前预测的任务中特别有用。例如，在对话式人工智能 （AI） 系统中，停止序列可以是对话结束标记或指示响应结束的特定短语。

Stop sequences can be predefined or dynamically generated based on the input or the generated output itself. In some cases, multiple stop sequences can be specified, allowing the model to stop generation upon encountering any of the defined sequences.
停止序列可以是预定义的，也可以根据输入或生成的输出本身动态生成。在某些情况下，可以指定多个停止序列，从而允许模型在遇到任何定义的序列时停止生成。


Be clear and concise.  简洁明了。
Prompts should be straightforward and avoid ambiguity. Clear prompts lead to more coherent responses. Craft prompts with natural, flowing language and coherent sentence structure. Avoid isolated keywords and phrases.
提示应简单明了，避免歧义。清晰的提示会导致更连贯的响应。用自然、流畅的语言和连贯的句子结构制作提示。避免使用孤立的关键字和短语。


Include context if needed.
如果需要，请包括 context。
Provide any additional context that would help the model respond accurately. For example, if you ask a model to analyze a business, include information about the type of business. What does the company do? This type of detail in the input provides more relevant output. The context that you provide can be common across multiple inputs or specific to each input.
提供有助于模型准确响应的任何其他上下文。例如，如果您要求模型分析业务，请包含有关业务类型的信息。公司是做什么的？输入中的此类详细信息提供了更相关的输出。您提供的上下文可以在多个输入中通用，也可以特定于每个输入。


Use directives for the appropriate response type. 对适当的响应类型使用 directives。
If you want a particular output form, such as a summary, question, or poem, specify the response type directly. You can also limit responses by length, format, included information, excluded information, and more.
如果需要特定的输出形式，如摘要、问题或诗歌，请直接指定响应类型。您还可以按长度、格式、包含的信息、排除的信息等来限制响应。


Use directives for the appropriate response type.
对适当的响应类型使用 directives。
If you want a particular output form, such as a summary, question, or poem, specify the response type directly. You can also limit responses by length, format, included information, excluded information, and more.
如果需要特定的输出形式，如摘要、问题或诗歌，请直接指定响应类型。您还可以按长度、格式、包含的信息、排除的信息等来限制响应。


Consider the output in the prompt.
请考虑提示符中的输出。
Mention the requested output at the end of the prompt to keep the model focused on appropriate content.
在提示末尾提及请求的输出，以使模型专注于适当的内容。


Start prompts with an interrogation.
以询问开始提示。
Phrase your input as a question, beginning with words, such as who, what, where, when, why, and how.
将您的输入表述为问题，以单词开头，例如谁、什么、在哪里、何时、为什么和如何。


Provide an example response.
提供示例响应。
Use the expected output format as an example response in the prompt. Surround it in brackets to make it clear that it is an example.
使用预期的输出格式作为提示中的示例响应。将其括在括号中以清楚地表明它是一个示例。


Break up complex tasks.  分解复杂的任务。
Foundation models can get confused when asked to perform complex tasks. Break up complex tasks by using the following techniques:
当要求执行复杂任务时，Foundation 模型可能会感到困惑。使用以下技术分解复杂的任务：

Divide the task into several subtasks. If you cannot get reliable results, try splitting the task into multiple prompts.
将任务划分为多个子任务。如果您无法获得可靠的结果，请尝试将任务拆分为多个提示。
Ask the model if it understood your instruction. Provide clarification based on the model's response.
询问模型是否理解您的指示。根据模型的响应提供说明。
If you don’t know how to break the task into subtasks, ask the model to think step by step. You will learn more about this type of prompt technique later on in this course. This method might not work for all models, but you can try to rephrase the instructions in a way that makes sense for the task. For example, you might request that the model divides the task into subtasks, approaches the problem systematically, or reasons through the problem one step at a time.
如果您不知道如何将任务分解为子任务，请让模型逐步思考。您将在本课程的后面部分了解有关此类提示技术的更多信息。此方法可能不适用于所有模型，但您可以尝试以对任务有意义的方式重新表述说明。例如，您可以要求模型将任务划分为多个子任务，系统地处理问题，或者一次一步地推理问题。


Experiment and be creative.
尝试并发挥创造力。
Try different prompts to optimize the model's responses. Determine which prompts achieve effective results and which prompts achieve inaccurate results. Adjust your prompts accordingly. Novel and thought-provoking prompts can lead to innovative outcomes.
尝试不同的提示来优化模型的响应。确定哪些提示获得有效的结果，哪些提示获得不准确的结果。相应地调整您的提示。新颖和发人深省的提示可以带来创新的结果。


Use prompt templates.  使用提示模板。
Prompt templates are predefined structures or formats that can be used to provide consistent inputs to FMs. They help ensure that the prompts are phrased in a way that is easily understood by the model and can lead to more reliable and higher-quality outputs. Prompt templates often include instructions, context, examples, and placeholders for information relevant to the task at hand.
提示模板是预定义的结构或格式，可用于为 FM 提供一致的输入。它们有助于确保以模型易于理解的方式表达提示，并且可以产生更可靠和更高质量的输出。提示模板通常包括说明、上下文、示例和占位符，用于显示与手头任务相关的信息。
Prompt templates can help streamline the process of interacting with models, making it easier to integrate them into various applications and workflows.
提示模板有助于简化与模型交互的过程，从而更轻松地将它们集成到各种应用程序和工作流中。

