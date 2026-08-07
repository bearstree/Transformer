### Notes from [Huggin Face LLM Courses](https://huggingface.co/learn/llm-course/en/):  
1. $\color{red}{\text{}}$ Transformers are **big**, **language models**. Broadly, they can be grouped into three categories:  
&emsp; a. GPT-like (also called **auto-regressive** Transformer models)  
&emsp; b. BERT-like (also called **auto-encoding** Transformer models)  
&emsp; c. T5-like (also called **sequence-to-sequence** Transformer models)  

1. All the Transformer models mentioned above (GPT, BERT, T5, etc.) have been trained as language models. This means they **have been trained on large amounts of raw text** in a **self-supervised fashion.**

1. $\color{red}{\text{Self-supervised learning}}$ is a type of training in which the **objective is automatically computed** from the inputs of the model. That means that humans are not needed to label the data:  
 &emsp; a. $\color{red}{\text{causal language modeling(CLM)}}$. Used by decoder models like GPT, this approach predicts the next token based on all previous tokens in the sequence. The model can only use context from the left (previous tokens) to predict the next token.  
 &emsp; b. $\color{red}{\text{Masked language modeling (MLM)}}$. Used by encoder models like BERT, this approach randomly masks some tokens in the input and trains the model to predict the original tokens based on the surrounding context. This allows the model to learn bidirectional context (looking at words both before and after the masked word).

1. Apart from a few outliers (like DistilBERT), the general strategy to achieve better performance is by increasing the models’ sizes as well as the amount of data they are pretrained on.

1. $\color{red}{\text{Transfer Learning}}$ pretrained on large amounts of text data in a self-supervised manner (without human annotations), then fine-tuned on specific tasks.  
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
Language models generally fall into three architectural categories:  
&emsp; **a. Encoder-only models**(like BERT): These models use a bidirectional approach to understand context from both directions. They’re best suited for tasks that require deep understanding of text, such as classification, named entity recognition, and question answering.  
&emsp; **b. Decoder-only models**(like GPT, Llama): These models process text from left to right and are particularly good at text generation tasks. They can complete sentences, write essays, or even generate code based on a prompt.  
&emsp; **c. Encoder-decoder models or sequence-to-sequence models**(like T5, BART): These models combine both approaches, using an encoder to understand the input and a decoder to generate output. They excel at sequence-to-sequence tasks like translation, summarization, and question answering.    
&emsp; **Attention layers**: tell the model to pay specific attention to certain words in the sentence you passed it (and more or less ignore the others) when dealing with the representation of each word.  
![Alt text](image/transformers_architecture.png)
*From HuggingFace LLM course*

1. $\color{red}{\text{Architectures vs. checkpoints}}$  
&emsp; **Architecture**: This is the skeleton of the model — the definition of each layer and each operation that happens within the model.  
&emsp; **Checkpoints**: These are the weights that will be loaded in a given architecture.  
&emsp; **Model**: This is an umbrella term that isn’t as precise as “architecture” or “checkpoint”: it can mean both. This course will specify architecture or checkpoint when it matters to reduce ambiguity.  

![Alt text](image/transformer_message_flow_verified.gif)


