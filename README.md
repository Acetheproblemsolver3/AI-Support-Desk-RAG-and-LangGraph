# AI Support Desk: Ticket Categorization using RAG and LangGraph

## Project Overview

This project implements a **Retrieval-Augmented Generation (RAG) based support ticket categorization system** using **LangGraph**. The system retrieves similar historical support tickets from a vector database and uses a language model to classify new incoming support tickets into appropriate categories.

The workflow combines **vector similarity search, contextual retrieval, and LLM reasoning** to improve the accuracy of ticket classification.

---

## System Architecture

```
User Ticket
     ↓
Preprocessing
     ↓
Embedding Generation
     ↓
Vector Database (Similarity Search)
     ↓
Retriever
     ↓
LLM Reasoning
     ↓
Ticket Category Prediction
```

LangGraph is used to orchestrate the workflow as a **stateful agent pipeline**, enabling modular and extensible processing steps.

---

## Key Components

### Data Processing
- Load and preprocess support ticket dataset
- Clean and prepare text data for embeddings

### Embeddings
- Generate semantic embeddings using Sentence Transformers

### Vector Database
- Store ticket embeddings in FAISS for similarity search

### Retriever
- Retrieve the most similar historical tickets

### RAG Pipeline
- Augment the query with retrieved ticket context

### LangGraph Workflow
- Build a graph-based pipeline with nodes for:
  - Retrieval
  - LLM reasoning
  - Decision logic

---

## Technologies Used

- Python
- LangGraph
- LangChain
- FAISS
- Sentence Transformers
- Jupyter Notebook

---

## Example Output

**Input Ticket**

```
"My wifi keeps disconnecting frequently"
```

**Predicted Category**

```
Network Issue
```

---

## Next Steps (Future Improvements)

While this project focuses on implementing the core RAG-based classification pipeline, several extensions could enhance it further.

### Multi-Agent Workflow

Future versions could introduce specialized agents to handle different stages of ticket processing.

```
Ticket Input
     ↓
Classifier Agent
     ↓
Troubleshooter Agent
     ↓
Resolution Generator
```

### Memory and User Context

The system could track repeated tickets from the same user to identify recurring issues and improve troubleshooting recommendations.

### Escalation and Routing Agents

Additional agents could automatically route tickets to appropriate support teams based on severity or issue type.

```
Agent 1 → Categorize ticket  
Agent 2 → Determine severity  
Agent 3 → Route ticket to support team
```

### Automated Ticket Resolution

The system could retrieve solutions from historical tickets and suggest fixes automatically.

```
Ticket → Retrieve solution → Suggest resolution
```

### Automated Knowledge Base Creation

Past support tickets could be stored in a vector database to create a continuously evolving support knowledge base.

```
Tickets → Embeddings → Vector Database → Searchable Knowledge Base
```

### User Interface

A lightweight user interface using **Streamlit** could allow users to submit tickets and view predicted categories and recommended solutions.

### Dynamic Category Discovery

Clustering techniques could be used to automatically detect new support ticket categories as new types of issues emerge.

---

## Repository Structure

```
project-root
│
├── data
│   └── support_ticket_data.csv
│
├── notebooks
│   └── ticket_rag_langgraph.ipynb
│
├── README.md
```

---

## Project Scope

This project focuses specifically on **building the RAG pipeline and LangGraph orchestration for ticket categorization**. Additional features such as multi-agent workflows, automated resolution systems, and UI interfaces are listed as future improvements.
