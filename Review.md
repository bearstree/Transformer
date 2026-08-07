### Notes from [Huggin Face LLM Courses](https://huggingface.co/learn/llm-course/en/):  
1. $\color{red}{\text{}}$ Transformers are **big**, **language models**. Broadly, they can be grouped into three categories:  
&emsp; a. GPT-like (also called **auto-regressive** Transformer models)  
&emsp; b. BERT-like (also called **auto-encoding** Transformer models)  
&emsp; c. T5-like (also called **sequence-to-sequence** Transformer models)  

1. All the Transformer models mentioned above (GPT, BERT, T5, etc.) have been trained as language models. This means they **have been trained on large amounts of raw text** in a **self-supervised fashion.**

1. $\color{red}{\text{Self-supervised learning}}$ is a type of training in which the **objective is automatically computed** from the inputs of the model. That means that humans are not needed to label the data:  
 &emsp; a. An example of a task is predicting the next word in a sentence having read the n previous words. This is called $\color{red}{\text{causal language modeling}}$ because the output depends on the past and present inputs, but not the future ones.  
 &emsp; b. Another example is $\color{red}{\text{masked language modeling}}$, in which the model predicts a masked word in the sentence.

1. Apart from a few outliers (like DistilBERT), the general strategy to achieve better performance is by increasing the models’ sizes as well as the amount of data they are pretrained on.

1. $\color{red}{\text{Transfer Learning}}$  
&emsp; a. **Pre-training** is the act of training a model from scratch: the weights are randomly initialized, and the training starts without any prior knowledge.  
&emsp; b. **Fine-tuning**, on the other hand, is the training done after a model has been pretrained. To perform fine-tuning, you first acquire a pretrained language model, then perform additional training with a dataset specific to your task.

1. Why **NOT** simply train the model for your final use case from the start (scratch)? There are a couple of reasons:  
&emsp; a. The pretrained model was already trained on a dataset that has some similarities with the fine-tuning dataset. The fine-tuning process is thus able to **take advantage of** knowledge acquired by the initial model during pretraining (for instance, with NLP problems, the pretrained model will have some kind of statistical understanding of the language you are using for your task).  
&emsp; b. Since the pretrained model was already trained on lots of data, the fine-tuning **requires way less data** to get decent results.  
&emsp; c. For the same reason, the **amount of time and resources needed to get good results** are much lower.  
For example, one could leverage a pretrained model trained on the English language and then fine-tune it on an arXiv corpus, resulting in a science/research-based model. The fine-tuning will only require a limited amount of data: the knowledge the pretrained model has acquired is “transferred,” hence the term transfer learning.
Fine-tuning a model therefore has lower time, data, financial, and environmental costs. It is also quicker and easier to iterate over different fine-tuning schemes, as the training is less constraining than a full pretraining.

1. $\color{red}{\text{General Transformer architecture}}$  
The model is primarily composed of two blocks:  
&emsp; **Encoder (left)**: The encoder receives an input and builds a representation of it (its features). This means that the model is optimized to acquire understanding from the input.  
&emsp; **Decoder (right)**: The decoder uses the encoder’s representation (features) along with other inputs to generate a target sequence. This means that the model is optimized for generating outputs.  
Each of these parts can be used independently, depending on the task:  
&emsp; a. Encoder-only models: Good for tasks that require understanding of the input, such as sentence classification and named entity recognition.  
&emsp; b. Decoder-only models: Good for generative tasks such as text generation.  
&emsp; c. Encoder-decoder models or sequence-to-sequence models: Good for generative tasks that require an input, such as translation or summarization.  
&emsp; **Attention layers**: tell the model to pay specific attention to certain words in the sentence you passed it (and more or less ignore the others) when dealing with the representation of each word.  

1. $\color{red}{\text{Architectures vs. checkpoints}}$  
&emsp; **Architecture**: This is the skeleton of the model — the definition of each layer and each operation that happens within the model.  
&emsp; **Checkpoints**: These are the weights that will be loaded in a given architecture.  
&emsp; **Model**: This is an umbrella term that isn’t as precise as “architecture” or “checkpoint”: it can mean both. This course will specify architecture or checkpoint when it matters to reduce ambiguity.  

![Alt text](image/transformer_message_flow_verified.gif)


