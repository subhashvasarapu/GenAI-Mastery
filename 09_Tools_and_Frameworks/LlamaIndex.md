
---

````markdown
# 🦙 LlamaIndex (GPT Index) Overview

**LlamaIndex** (previously known as GPT Index) is a powerful framework that enables **LLMs to query and reason over your custom data** like PDFs, Notion docs, SQL, CSVs, and more.

It bridges the gap between **unstructured or structured data sources** and large language models (LLMs) by building intelligent indexes and retrieval pipelines.

---

## 🧠 What is LlamaIndex?

LlamaIndex provides tools to:
- Ingest and parse documents
- Index documents into LLM-friendly formats
- Query the index using natural language
- Retrieve and summarize relevant information

---

## 🔧 Installation

```bash
pip install llama-index openai
````

Optional extras:

```bash
pip install llama-index[docarray,faiss,pinecone]
```

---

## 📂 Simple Workflow

```
Documents → Parsing → Indexing → Querying via LLM
```

---

## 🔁 Step-by-Step Example

### 1. Load Documents

```python
from llama_index import SimpleDirectoryReader

documents = SimpleDirectoryReader("data").load_data()
```

### 2. Build the Index

```python
from llama_index import GPTSimpleVectorIndex

index = GPTSimpleVectorIndex.from_documents(documents)
index.save_to_disk("index.json")
```

### 3. Query the Index

```python
from llama_index import GPTSimpleVectorIndex

index = GPTSimpleVectorIndex.load_from_disk("index.json")
response = index.query("Summarize the key points from the report.")
print(response)
```

---

## 💡 Use Case Examples

| Use Case                    | How LlamaIndex Helps                          |
| --------------------------- | --------------------------------------------- |
| Chat with PDFs              | Ingest PDFs and ask questions with GPT        |
| Company Knowledge Base      | Index Notion/Google Docs, internal docs, etc. |
| Academic Research Assistant | Query over scientific papers or datasets      |
| Law/Policy Analysis         | Summarize legal documents and precedents      |

---

## 🧩 Types of Indexes

| Index Type          | Description                                   |
| ------------------- | --------------------------------------------- |
| `VectorIndex`       | Store vector embeddings for similarity search |
| `ListIndex`         | Maintains order — good for timeline queries   |
| `TreeIndex`         | Hierarchical summarization across docs        |
| `KeywordTableIndex` | Keyword-based semantic lookup                 |

---

## 🔍 Advanced Features

* 🔁 **Retriever & Query Engines**: Plug in custom retrieval logic (e.g., top-k, hybrid).
* 📦 **StorageContext**: Store and reuse indices efficiently.
* 🧠 **Callbacks**: Monitor and trace LLM usage.
* 🧰 **Integrations**:

  * FAISS / Chroma / Pinecone for vector DBs
  * LangChain for agents & tools
  * Streamlit, Gradio for UI

---

## 🧪 LangChain + LlamaIndex Combo

```python
from langchain.llms import OpenAI
from llama_index.langchain_helpers.chain_wrapper import LLMPredictor

llm_predictor = LLMPredictor(llm=OpenAI(temperature=0))
```

> LlamaIndex can be used as a document retriever within LangChain for long-form conversations or search-based Q\&A.

---

## 📌 Summary

| Feature                   | Description                                  |
| ------------------------- | -------------------------------------------- |
| Custom Document Ingestion | Work with PDFs, CSVs, Markdown, Notion, etc. |
| LLM-Optimized Indexing    | Builds smart indexes for GPT-style models    |
| Natural Language Query    | Ask questions in plain English over any data |
| Open Ecosystem            | Works with LangChain, FAISS, Pinecone, etc.  |

---

> 🧠 LlamaIndex turns your private or custom data into a searchable brain that LLMs can query intelligently.
