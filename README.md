minimal Retrieval-Augmented Generation system 

A RAG system combines 2 things:

- a retriever : finds useful information from a database > we use NumPy for document indexing + cosine similarity retrieval 
- a generator : writes the answer using retrieved information > we use mistralai-small-3.1

We need RAG because LLMs internal knowledge can be incomplete or incorrect (ex: training cutoff, private information)

features:

- tokenizer
- numpy vector database
- retrieve_topk function usine cosine similarity between question and vectordb documents
- rag_answer function leverage system and user message to restrict mistralai-small context to our retrieved documents

We illustrate our architecture by designing a knowledge base made of customer information.

Our system gives customer support / sales the exact status of every customer relationship. The LLM generation enables to extract knowledge from and analyze large amounts of text data.

example question: "Hey I am a new sales person I want to understand James commercial history in order to prepare my incoming call with him. What should I offer him?"

retrieval-augmented answer: 

RETRIEVED:
[sim=0.262] Customer ID: CUST002 | Name: James Turner | Age: 45 | Subscription Tier: Basic | Joined: 2022-10-02 | Last Payment: 2025-11-15 | Payment Status: Late last month but now settled | Claims: 0 | Support Notes: ((2023-06-02) Interested in upgrading next year. ; (2024-05-12) Declined sales team special Premium tier offer. ; (2024-05-17) Complained about Basic tier limitations ; (2025-01-06) Asked for a Premium Tier discount, rejected by sales team 

ANSWER:
Based on the context, James Turner has shown interest in upgrading his subscription tier but has also declined a special offer and asked for a discount which was refused. He has complained about the limitations of the Basic tier. Given this information, you might want to:

1. Acknowledge his previous interest in upgrading.
2. Address his concerns about the Basic tier limitations.
3. Offer him the Premium tier again, but this time, you could consider offering a limited-time discount or highlighting the benefits and features of the Premium tier that would address his concerns.
4. Be prepared to discuss any specific features or services he is interested in and how the Premium tier can meet his needs.

You don't know if he has any specific needs or preferences beyond what's mentioned, so focus on the information provided.
