Zero-shot prompting is a technique where a user presents a task to a generative model without providing any examples or explicit training for that specific task. In this approach, the user relies on the model's general knowledge and capabilities to understand and carry out the task without any prior exposure, or shots, of similar tasks. Remarkably, modern FMs have demonstrated impressive zero-shot performance, effectively tackling tasks thatthey were not explicitly trained for.
零样本提示是一种技术，用户向生成模型展示任务，而不为该特定任务提供任何示例或明确训练。在这种方法中，用户依靠模型的一般知识和能力来理解和执行任务，而无需事先接触或拍摄任何类似任务。值得注意的是，现代 FM 已经展示了令人印象深刻的零射击性能，有效地处理了他们没有接受过明确培训的任务。

To optimize zero-shot prompting, consider the following tips:
要优化 zero-shot 提示，请考虑以下提示：

• The larger and more capable the FM, the higher the likelihood of obtaining effective results from zero-shot prompts.
FM 越大、功能越强大，从零发提示中获得有效结果的可能性就越高。

• Instruction tuning, a process of fine-tuning models to better align with human preferences, can enhance zero-shot learning capabilities. One approach to scale instruction tuning is through reinforcement learning from human feedback (RLHF), where the model is iteratively trained based on human evaluations of its outputs.
指令调整是微调模型以更好地符合人类偏好的过程，可以增强零样本学习能力。扩展指令调优的一种方法是通过来自人类反馈的强化学习 （RLHF），其中模型根据人类对其输出的评估进行迭代训练。


Few-shot prompting is a technique that involves providing a language model with contextual examples to guide its understanding and expected output for a specific task. In this approach, you supplement the prompt with sample inputs and their corresponding desired outputs, effectively giving the model a few shots or demonstrations to condition it for the requested task. Although few-shot prompting provides a model with multiple examples, you can also use single-shot or one-shot prompting by providing just one example.
Few-shot prompting 是一种技术，涉及为语言模型提供上下文示例，以指导其理解和特定任务的预期输出。在这种方法中，您可以使用样本输入及其相应的所需输出来补充提示，从而有效地为模型提供一些镜头或演示，以使其适应请求的任务。尽管 few-shot 提示为模型提供了多个示例，但您也可以通过仅提供一个示例来使用 single-shot 或 one-shot prompting。

When employing a few-shot prompting technique, consider the following tips:
在采用 Few-shot 提示技术时，请考虑以下提示：

• Make sure to select examples that are representative of the task that you want the model to perform and cover a diverse range of inputs and outputs. Additionally, aim to use clear and concise examples that accurately demonstrate the desired behavior.
确保选择能够代表您希望模型执行的任务并涵盖各种输入和输出的示例。此外，目标是使用清晰简洁的示例来准确演示所需的行为。

• Experiment with the number of examples. The optimal number of examples to include in a few-shot prompt can vary depending on the task, the model, and the complexity of the examples themselves. Generally, providing more examples can help the model better understand the task. But too many examples might introduce noise or confusion.
尝试示例的数量。要包含在 Few-shot Prompt 中的最佳示例数量可能因任务、模型和示例本身的复杂程度而异。通常，提供更多示例可以帮助模型更好地理解任务。但是太多的例子可能会带来噪音或混淆。


Chain-of-thought (CoT) prompting is a technique that divides intricate reasoning tasks into smaller, intermediary steps. This approach can be employed using either zero-shot or few-shot prompting techniques.  CoT prompts are tailored to specific problem types. To initiate the chain-of-thought reasoning process in a machine learning model, you can use the phrase "Think step by step." It is recommended to use CoT prompting when the task requires multiple steps or a series of logical reasoning.
思维链 （CoT） 提示是一种将复杂的推理任务划分为更小的中间步骤的技术。这种方法可以使用零镜头或少镜头提示技术来采用。 CoT 提示是针对特定问题类型量身定制的。要在机器学习模型中启动思维链推理过程，您可以使用短语“Think step by step”。当任务需要多个步骤或一系列逻辑推理时，建议使用 CoT 提示。


An organization is using a generative model to solve complex mathematical word problems. The prompt used must break down the problem, identify relevant information, and apply appropriate problem-solving strategies and calculations.
组织正在使用生成模型来解决复杂的数学单词问题。使用的提示必须分解问题，识别相关信息，并应用适当的问题解决策略和计算。

Chain-of-thought prompting combined with few-shot prompting: Prompt the model to break down the problem-solving process into a series of logical steps, and include a few examples of solved word problems.
链式思维提示与少数镜头提示相结合：提示模型将解决问题的过程分解为一系列逻辑步骤，并包括一些已解决的单词问题的示例。
