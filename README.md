# AI Support Desk: RAG-Based Ticket Categorization with LangGraph

## System Architecture

```text
                +---------------------+
                |   User Support      |
                |      Ticket         |
                +----------+----------+
                           |
                           v
                 +-------------------+
                 |  Embedding Model  |
                 | SentenceTransform |
                 +---------+---------+
                           |
                           v
                 +-------------------+
                 |   Vector Database |
                 |       FAISS       |
                 +---------+---------+
                           |
                           v
                 +-------------------+
                 |   Retriever Node  |
                 | (Similar Tickets) |
                 +---------+---------+
                           |
                           v
                 +-------------------+
                 |   Reasoning Node  |
                 |      (LLM)        |
                 +---------+---------+
                           |
                           v
                 +-------------------+
                 | Structured Output |
                 | Category, Tags,   |
                 | Priority, ETA     |
                 +-------------------+
```

---

# Project Overview

This project implements a **Retrieval-Augmented Generation (RAG) based support ticket categorization system** using **LangGraph**.

The system retrieves similar historical support tickets from a **vector database** and uses a **Large Language Model (LLM)** to classify incoming tickets and generate structured support metadata.

The system outputs structured information such as:

- Ticket Category
- Tags
- Priority Level
- Estimated Resolution Time (ETA)
- Automated Support Response

This project demonstrates how **vector search, LLM reasoning, and workflow orchestration** can be combined to build an intelligent support automation system.

---

# LangGraph Workflow

```text
Ticket Input
     ↓
Retriever Node
     ↓
Reasoning Node (LLM)
     ↓
Structured Ticket Output
```

Each node updates the shared **workflow state**, allowing modular and scalable AI pipelines.

---

# Key Components

## Data Processing

- Load and preprocess support ticket dataset
- Clean and prepare text for embeddings

## Embeddings

Semantic embeddings are generated using **Sentence Transformers**.

## Vector Database

Ticket embeddings are stored in **FAISS** to enable fast similarity search.

## Retriever

The retriever identifies **historically similar tickets** that provide context for the LLM.

## RAG Pipeline

Retrieved tickets are injected into the prompt as context to improve classification accuracy.

## LangGraph Workflow

The system is orchestrated using **LangGraph**, which organizes the workflow into nodes:

- Retriever Node
- Reasoning Node
- Decision Logic

---

# Structured Ticket Output

The LLM generates structured JSON which is parsed into a support ticket table.

Example:

| Ticket ID | Category | Tags | Priority | ETA | Response |
|----------|----------|------|----------|------|---------|
| ST2023-007 | Hardware Issues | Laptop, Restart | High | 24 hours | Please restart the device and check hardware connections |
| ST2023-008 | Data Recovery | Data loss, documents | High | Immediate | Please avoid using the device further and contact support |

This demonstrates how **LLM outputs can automatically populate support ticket metadata**.

---

# Technologies Used

- Python
- LangGraph
- LangChain
- FAISS
- Sentence Transformers
- OpenAI API
- Jupyter Notebook

---

# Repository Structure

```text
project-root
│
├── data
│   └── support_ticket_data.csv
│
├── notebooks
│   └── rag_ticket_langgraph.ipynb
│
└── README.md
```

---

# Running the Project

Install dependencies

```bash
pip install langgraph langchain faiss-cpu sentence-transformers openai
```

Run the notebook

```bash
rag_ticket_langgraph.ipynb
```

---

# Example Usage

Input Ticket

```
"My laptop refuses to start"
```

Example Output

```
Category: Hardware Issues
Priority: High
ETA: 24 hours
Suggested Response: Please restart the laptop and ensure hardware connections are secure.
```

---

# Next Steps (Future Improvements)

This project focuses on the **core RAG pipeline and LangGraph orchestration**. Future improvements could extend the system further.

## Multi-Agent Workflow

```
Ticket
  ↓
Classifier Agent
  ↓
Troubleshooter Agent
  ↓
Resolution Generator
```

## User Memory

Track repeated issues from the same user to detect recurring technical problems.

## Ticket Routing

Automatically route tickets to appropriate support teams.

## Knowledge Base Creation

Store resolved tickets in a vector database to build a searchable support knowledge base.

## User Interface

A lightweight UI using **Streamlit** could allow users to submit tickets and receive automated assistance.

---

# Project Scope

This project focuses on building a **RAG-based ticket categorization system using LangGraph**. Advanced features such as multi-agent workflows and UI interfaces are intentionally left as future enhancements.
