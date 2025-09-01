# RAG for Financial Reports in Python

## Task Description
This project implements a Retrieval-Augmented Generation (RAG) system using annual reports from ASUS from 2020 to 2024 as the knowledge base. These reports contain fact-dense, proprietary, and up-to-date information on ASUS’s financials, ESG strategies, product developments, and governance policies—data that general-purpose LLMs are unlikely to cover during pretraining.  

The goal is to enable accurate, document-grounded question answering on company-specific topics, such as financial performance, ESG actions, and governance priorities.

## Approach
- **Data sourcing**: Collected ASUS annual reports from 2020 to 2024 in PDF format.  
- **Preprocessing**: Split reports into chunks of ~1000 tokens with overlap to preserve context.  
- **Embedding**: Generated vector embeddings using OpenAI’s `text-embedding-3-small`.  
- **Vector store**: Stored embeddings in Chroma for efficient retrieval.  
- **Retrieval pipeline**:  
  - Implemented multi-vector retriever (embedding + summary-based retrieval).  
  - Applied Hypothetical Document Embeddings (HyDE) to improve recall.  
  - Integrated a self-critic loop to refine generated answers.  
- **Query answering**: Combined retrieved documents with LLM responses to deliver fact-grounded answers.

## Results
- Successfully retrieved and answered queries regarding ASUS financial metrics (e.g., 2023 net profit, EPS), ESG initiatives, and governance principles.  
- Multi-vector retrieval improved coverage of both numeric KPIs and textual policy content.  
- HyDE and self-critic mechanisms reduced semantic drift, leading to more accurate and relevant responses.  

## Challenges & Learnings
- **Hybrid content**: Annual reports mix structured tables with unstructured text, requiring careful preprocessing and chunking.  
- **Query ambiguity**: User questions like “How did ASUS perform in ESG?” are broad; retrieval strategies had to balance recall and precision.  
- **Evaluation difficulty**: Measuring answer accuracy required manual cross-checking against source documents, as automatic evaluation metrics are less reliable in factual QA.  

## Tech Stack
- Python  
- LangChain  
- OpenAI embeddings (`text-embedding-3-small`)  
- Chroma (vector database)  
- HyDE, self-critic RAG loop  

