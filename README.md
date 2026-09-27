HireFlow - Intelligent Candidate Search and Evaluation
Combining Semantic Search with Generative AI for Intelligent Candidate Matching
Project Context
This project offers learners the opportunity to:
Build a RAG pipeline for semantic document matching
Apply embedding models for retrieval
Use prompt engineering to generate explainable candidate evaluations
Design modular and scalable AI systems for enterprise use
Implement evaluation metrics for relevance and interpretability
 
Data: 
Resume dataset (PDF) parsed into structured text + metadata 
Job descriptions from various domains for testing semantic matching
Note:
All data in this dataset are synthetically generated for research and testing purposes. Any similarity to actual persons, companies, or events is entirely coincidental and unintended.
Technical Requirements
Dependencies:
Python 3.12+ 
Gemini API (for LLM and embeddings)
FAISS / Pinecone (vector database)
Pandas (resume data handling)
Streamlit (for recruiter UI)
Pydantic (data validation)
Python-dotenv (environment configuration)




User Interface (Data Storage)
Document Processor
Indexing & Storage
Search - Retrieval
Result Processing
Enhancement - Reranking, Evaluation
LLM Generation - O/p Parser
Quality Assessment
Memory

Streamlit - UI - Presentation Layer
Core - Business Layer/ Business Logic
Data - Data Storage Layer

HireFlow/
├── core/
│   ├── ingestion.py        # Load resume and job description PDFs as Documents
│   ├── parsing.py          # LLM-based resume / job description parsing
│   ├── vector_store.py     # Pinecone indexing and semantic search
│   ├── hybrid_indexer.py   # BM25 keyword search + vector search, combined
│   ├── search_router.py    # Routes queries to shallow or deep search
│   ├── re_ranker.py        # AI evaluation of candidate fit
│   ├── evaluator.py        # RAGAS quality evaluation
│   └── memory_rag.py       # Search history for the session
├── utils/
│   ├── config.py           # Configuration (reads .env)
│   ├── schemas.py          # Pydantic data models
│   ├── multi_query.py      # Rewrites a query several ways
│   └── utils.py            # PDF loading, embeddings, rate limiter, filters
├── streamlit/
│   └── app.py              # Web interface
├── data/
│   ├── resumes/            # 50 sample resume PDFs
│   └── jds/                # Sample job description
├── main.py                 # Command-line demo
└── HOMEWORK.md             # The homework - start here after setup



Create project directory


mkdir hireflow
cd hireflow

# Create the modular structure
mkdir -p core data/resumes data/hybrid_index data/memory streamlit

# Create essential files
touch config.py utils.py main.py requirements.txt .env
touch core/__init__.py core/ingestion.py core/parsing.py
touch core/vector_store.py core/hybrid_indexer.py core/re_ranker.py
touch core/memory_rag.py core/evaluator.py core/filters.py
touch streamlit/app.py


Requirements.txt

python-dotenv>=1.0
pydantic[email]>=2.7,<3
pydantic-settings>=2.3
langchain-core>=1.0,<2
langchain-classic>=1.0
langchain-text-splitters>=1.0
langchain-google-genai>=3.0
# langchain-community stays below 0.4: ragas 0.4.x imports a module that 0.4 removed.
langchain-community>=0.3,<0.4
pinecone>=7.0
pypdf>=5.0
rank-bm25>=0.2.2
pandas>=2.0
streamlit>=1.40
ragas>=0.4,<0.5

