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
