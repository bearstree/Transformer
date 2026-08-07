### Notes from [Huggin Face LLM Courses](https://huggingface.co/learn/llm-course/en/):  

1. $\color{red}{\text{Encoder models}}$ use only the encoder of a Transformer model. At each stage, the attention layers can access all the words in the initial sentence. 
These models are often characterized as having “bi-directional” attention, and are often called auto-encoding models.
Encoder models are best suited for tasks requiring an understanding of the full sentence, such as sentence classification, named entity recognition (and more generally word classification),
and extractive question answering. Representatives:  
&emsp; BERT  
&emsp; DistilBERT  
&emsp; ModernBERT  

1.  $\color{red}{\text{Decoder models}}$ use only the decoder of a Transformer model. At each stage, for a given word the attention layers can only access the words positioned before it in the sentence.
These models are often called auto-regressive models. The pretraining of decoder models usually revolves around predicting the next word in the sentence. Representatives:  
&emsp; Hugging Face SmolLM Series  
&emsp; Meta’s Llama Series  
&emsp; Google’s Gemma Series  
&emsp; DeepSeek’s V3  

1.   $\color{red}{\text{Modern Large Language Models (LLMs)}}$ Most of them use the decoder-only architecture, trained in two phases:  
&emsp; **Pretraining**: The model learns to predict the next token on vast amounts of text data  
&emsp; **Instruction tuning**: The model is fine-tuned to follow instructions and generate helpful responses  

