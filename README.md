# Research Paper RAG Chatbot
AI-powered research assistant that answers questions about research papers using Retrieval-Augmented Generation (RAG).

## Features
- **PDF Ingestion**: Automatically process and index research papers
- **Hybrid Search**: Combines semantic and lexical search
- **Local LLM**: Uses Ollama for private, offline AI responses
- **Chat Interface**: Clean Streamlit web interface
- **Source Citations**: Shows which papers answers come from

## Architecture
PDF Files → Parser → Chunker → Embeddings → Vector DB → User Question → Retriever → LLM → Answer with Sources                  

## Prerequisites
- Python 3.8+
- [Ollama](https://ollama.ai) installed locally

## Project Structure
```
research-rag-chatbot/
├── data/
│   └── raw_pdfs/          # Put your PDFs here
├── src/
│   ├── ingestion/         # PDF processing pipeline
│   │   ├── pdf_parser.py      # PDF → Text
│   │   ├── chunker.py     # Text → Chunks
│   │   ├── embedder.py    # Text → Vectors
│   │   ├── vector_store.py       # Vector database
│   │   └── pipeline.py    # Orchestration
│   ├── retrieval/
│   │   └── retriever.py   # Search engine
│   └── generation/
│       ├── generator.py   # LLM integration
│       └── rag_chain.py   # Complete RAG
├── scripts/
│   ├── ingest.py         # Run ingestion
│   |
│   └── test_rag.py       # Test RAG system
├── app.py                 # Streamlit interface
├── requirements.txt
```

## Usage
### Step 1: Add Your PDFs

Place your research papers (PDF format) in the `data/raw_pdfs/` folder:
```bash
mkdir -p data/raw_pdfs
cp /path/to/your/papers/*.pdf data/raw_pdfs/
```

### Step 2: Ingest PDFs

Process your PDFs to create the vector database:
```bash
python scripts/ingest.py
```

**Expected output:**
```
Initializing Ingestion Pipeline...
Found 5 PDF(s)
...
Processed: 5
Total documents in DB: 250
```

### Step 3: Run the Chat Interface
```bash
streamlit run app.py
```

This opens a web interface at `http://localhost:8501`

### Step 4: Ask Questions!

Type questions like:
- "What is the attention mechanism?"
- "How does AI help in nutrition research?"
- "Explain the transformer architecture"
