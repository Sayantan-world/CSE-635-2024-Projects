# Project 1: LLMs for Societal Good

### Overview
The advances in deep learning combined with the availability of large, diverse corpora have led to significant progress in the field of conversational AI, commonly referred to as chatbots. The initial models were targeted at task-oriented applications such as customer service and relied on rule-based systems. Currently, there is the widespread use of commercial chatbots such as Alexa and Google. At the same time, these systems reflect more advanced machine learning technology, their intended use is primarily to inform, entertain and perform simple tasks for users.More recently, chatbots have been configured to be more empathetic and to reflect various personas in an attempt to engage more deeply with users; the term socialbots is now more commonly used. There has been an increased interest in using these socialbots for societal applications, including helping people with amnesia or those experiencing isolation.

The project is focused on leveraging Large Language Models (LLMs) for societal good, specifically through a Mental Health Support Chatbot. The background sets the stage for understanding this technology's critical importance and potential impact. Mental health issues have become a global crisis, affecting millions of people worldwide, with barriers such as stigma, accessibility, and lack of resources preventing many from receiving the help they need. In this context, LLMs offer a revolutionary approach to providing support. By harnessing the power of advanced natural language processing and understanding, these models can facilitate real-time, empathetic, and accessible mental health support across various languages and cultures. This project aims to bridge the gap between those in need and the vast resources available in the mental health domain. By developing a chatbot capable of understanding and responding to a wide range of emotional states and mental health concerns, the project showcases the technological capabilities of LLMs. It underscores the profound societal impact of AI, offering support for those who may feel isolated or misunderstood.

The aim of this project is to create an end-to-end conversational system (socialbot) that can engage in open-domain chit-chat and topical human-like conversations. The system should input a query text from the user and generate a text response befitting the query and conversation context. Ideally, your system should implement the following:
- “planning component” a.k.a dialogue manager (DM) which 
    - determines which generator(s) to invoke in a given conversational state
    - chooses the best response from a set of generated candidate responses. 


### Task: Empathetic Chatbot
**Definition:** Given a conversation’s context C and the current query Q, create a conversational system that yields the most suitable response R: the output of an IR-based model, a neural language model (LM) that learns the conditional distribution p(R|C, Q), or a combination of both. At every turn, the system must generate multiple candidate responses <R_a, R_b, ..., R_n>. A rule-based or neural dialogue manager (DM) should select the most appropriate response. All neural LMs should be trained by minimizing the language modeling loss between the generated response R and the golden response Y.

Your system should be able to:
- Classify emotion if required.
- Respond with empathy.
- Share opinions whenever required.
- Have Feedback Mechanism
- Share facts whenever suitable (movies, cooking, music, etc)
    - Movies dataset: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?select=keywords.csv
    - Cooking Dataset: https://www.kaggle.com/datasets/paultimothymooney/recipenlg


### Datasets
You are free to use any relevant dataset that you want. Here are some recommendations and one of them that you have to use.
- [Have to use] The Empathetic Dialogues (ED) dataset, which comprises 25k conversations grounded in emotional situations. (https://github.com/facebookresearch/EmpatheticDialogues).
- GoEmotions: https://blog.research.google/2021/10/goemotions-dataset-for-fine-grained.html
- DailyDialog: http://yanran.li/dailydialog
- https://www.kaggle.com/datasets/anthonytherrien/emotional-intelligence-booster-mistral-7b/data

### Evaluation Metrics:

##### Automatic Metrics
The following metrics should be calculated between the generated response in the test set and the golden response and applies only to the ED dataset. Each metric should be compared against suitable external and internal baselines.
- Perplexity (https://en.wikipedia.org/wiki/Perplexity)
- BLEU score (https://en.wikipedia.org/wiki/BLEU)
- ROUGE score (https://en.wikipedia.org/wiki/ROUGE_(metric))
- BERT Score (https://github.com/Tiiiger/bert_score)
- BLEURT Score (https://github.com/google-research/bleurt)

##### Human Evaluation
We will test your chatbot and rate it on a Likert scale of 1 (low) to 5 (high) on the following metrics:
- Fluency: Is the generated response natural, fluent and grammatically correct? This metric tests the syntax of the response.
- Coherence: Is the response appropriate w.r.t the query and context?
- Empathy: Does the response exude appropriate emotion?
- Factual: Is the response factually correct (if a fact is expected as a response)

### Bonus Points
- Make the socialbot Multilingual
    - FLORES: https://huggingface.co/datasets/facebook/flores
- Handles CodeMix (EMNLP 2023)
    - https://aclanthology.org/2023.emnlp-main.598/






