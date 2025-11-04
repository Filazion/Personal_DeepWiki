# 🤖 AI-Powered Repository Assistant — From Data Ingestion to Deployment  

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)
![OpenAI](https://img.shields.io/badge/OpenAI-API-green?logo=openai)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## 🧠 Overview  
I designed and implemented a complete **document-aware AI assistant** that can ingest any GitHub repository, index its documentation, and answer natural-language questions with file-level citations.  
This system brings together **data ingestion, intelligent chunking, hybrid search, and LLM-driven reasoning** into one deployable Streamlit application.

---

## 🎯 Problem Statement  
Developers and researchers often spend hours searching large codebases and documentation.  
Traditional keyword search doesn’t capture meaning or context — it can’t answer questions like *“Where is the authentication flow defined?”* or *“What does this API function do?”*  

I wanted to build an AI assistant that could:  
✅ Understand documentation contextually  
✅ Retrieve precise content chunks from repositories  
✅ Generate accurate, cited answers in real time  

---

## ⚙️ Key Features  
- 🧩 **GitHub ingestion pipeline** — downloads and parses repository markdown files via `Requests` + `Python-Frontmatter`.  
- 🧠 **Multi-strategy chunking** — sliding window, paragraph-based, and section-based splits to preserve meaning.  
- 🔎 **Hybrid search engine** — combines lexical search (`minsearch`) and semantic embeddings (`sentence-transformers`).  
- 🤝 **LLM-driven agent** — built using `Pydantic-AI` and OpenAI’s function-calling API with enforced citations.  
- 🧾 **Evaluation framework** — LLM-as-a-Judge scoring relevance, clarity, and completeness.  
- 💬 **Streamlit web app** — interactive interface with streaming responses, logs, and persistent chat history.  
- 📦 **Modular package design** — all logic separated into clean scripts (`ingest.py`, `search_tools.py`, `search_agent.py`, `logs.py`, `app.py`).  

---

## 🧩 Architecture  

      ┌────────────────────────────────────────┐
      │             GitHub Repo                 │
      └────────────────────────────────────────┘
                         │
                         ▼
             [ Data Ingestion Pipeline ]
               - Requests
               - Python-Frontmatter
                         │
                         ▼
           [ Intelligent Text Chunking ]
               - Section, paragraph, sliding
                         │
                         ▼
             [ Hybrid Search Index ]
         - minsearch (lexical)
         - sentence-transformers (semantic)
                         │
                         ▼
             [ AI Agent (Pydantic-AI) ]
         - OpenAI Function-Calling
         - Citation Enforcement
                         │
                         ▼
            [ Evaluation & Logging Layer ]
               - LLM-as-a-Judge
               - JSON logs via Pandas
                         │
                         ▼
            [ Streamlit Web Interface ]
               - Real-time Q&A
               - Chat history
               - API config

---

## 🧮 Approach  

1. **Data Ingestion**  
   - Downloaded and extracted markdown documentation directly from GitHub zip archives.  
   - Parsed metadata using `python-frontmatter` for file organization.  

2. **Chunking & Indexing**  
   - Implemented multiple chunking methods to prevent context loss.  
   - Indexed chunks via a **hybrid search** pipeline combining lexical (`minsearch`) and semantic (`sentence-transformers`) retrieval.  

3. **Agent Construction**  
   - Integrated **Pydantic-AI** for structured prompt handling and OpenAI function-calling.  
   - Enforced mandatory search before answering and added file-name citation requirement.  

4. **Evaluation & Logging**  
   - Built an LLM evaluation system (“LLM-as-a-Judge”) to automatically score each output.  
   - Logged query performance metrics (accuracy, latency, relevance) to JSON for Pandas analysis.  

5. **Deployment**  
   - Developed an interactive Streamlit dashboard with chat-based interface and streaming responses.  
   - Packaged as modular scripts for scalability and reuse across other repositories.  

---

## 🚀 Results  
| Metric | Value |
|--------|--------|
| **Repositories Processed** | [xx] |
| **Documents Indexed** | [xx] |
| **Average Evaluation Score** | [xx]% |
| **Query Latency** | [xx] seconds |

✅ Delivered a **production-ready assistant** capable of answering repository questions with full traceability.  
✅ Demonstrated [xx]% accuracy in identifying correct file sources.  
✅ Achieved significant improvements in search relevance over baseline keyword methods.

---

## 🖥️ Screenshots  

| Screenshot | Description |
|-------------|--------------|
| ![Dashboard](./ai-repo-assistant-dashboard.png) | Streamlit interface showing real-time answers with citations |
| ![Architecture](./ai-repo-assistant-architecture.png) | System pipeline from ingestion to deployment |
| ![Evaluation](./ai-repo-assistant-evals.png) | Evaluation results summarized with Pandas |

---

## 🧰 Tech Stack  
| Tool / Library | Purpose |
|-----------------|----------|
| **Python** | Core programming language |
| **OpenAI API** | LLM responses + function-calling |
| **Pydantic-AI** | Tool orchestration & structured prompts |
| **minsearch** | Lightweight lexical search engine |
| **sentence-transformers** | Semantic embeddings for retrieval |
| **Streamlit** | Web interface & app hosting |
| **Pandas** | Data logging and evaluation |
| **Requests** | GitHub API integration |
| **Python-Frontmatter** | Markdown metadata parsing |

---

## ⚙️ Installation & Usage  

### 1️⃣ Clone the Repository  
```bash
git clone https://github.com/[yourusername]/ai-repo-assistant.git
cd ai-repo-assistant
