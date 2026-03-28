# Building a Financial Knowledge Graph RAG Pipeline for Tech M&A Analysis
**Authors:** Ivan Delafuys - Hector Decugniere

This project demonstrates a complete data engineering and AI pipeline, transforming unstructured financial news into a structured Knowledge Graph (KG) and querying it via a local Retrieval-Augmented Generation (RAG) chatbot.

## Project Overview
The objective was to build a system capable of providing fact-checked answers regarding Technology Mergers and Acquisitions (M&A). The pipeline covers everything from web crawling to latent space visualization and interactive NLP querying.

### Key Features:
- **Phase 1: Information Extraction:** Automated crawling of 6 major tech newsrooms using `trafilatura` and entity extraction with the `en_core_web_trf` transformer model.
- **Phase 2: Knowledge Base Construction:** RDF construction using `rdflib` and a 3-step SPARQL expansion strategy to reach exactly 53,568 triplets.
- **Phase 3: Reasoning & KGE:** Logical reasoning using SWRL rules (HermiT) and training Knowledge Graph Embeddings (TransE and ComplEx).
- **Phase 4: RAG Pipeline:** A local Llama 3.2 1B model (via Ollama) generating and self-repairing SPARQL queries to fetch real-world facts from the graph.

## Performance Summary
After 50 training epochs, the **TransE** model achieved:
- **MRR:** 0.0371
- **Hits@10:** 0.0952

## Installation & Setup

1. **Clone the repository:**
   bash
   git clone [https://github.com/votre-nom/Financial-KG-RAG-Analysis.git](https://github.com/votre-nom/Financial-KG-RAG-Analysis.git)
   cd Financial-KG-RAG-Analysis

2. **Install Dependencies:**
    pip install -r requirements.txt
    python -m spacy download en_core_web_trf

3. **Configure Local LLM:**
    Install Ollama.
    Pull the required model: ollama pull llama3.2:1b.

4. **Run the Notebooks:**
    Open and execute the labs in sequence: Lab1.ipynb → Lab2.ipynb → Lab3.ipynb → Lab4.ipynb.

## Conclusion
This project demonstrates that while small local models (1B) have cognitive limits, a Knowledge Graph serves as a vital ground truth to prevent hallucinations.