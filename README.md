# Auto-RAG Pipeline Generator using Snowflake Cortex

## Overview

This project demonstrates a prototype implementation of a Retrieval-Augmented Generation (RAG) pipeline using Snowflake Cortex AI capabilities.

The system enables users to query enterprise knowledge sources such as policies, manuals, and support documentation using natural language.

Instead of manually searching documents, the system retrieves relevant document chunks and generates contextual answers using a large language model.

---

## Problem Statement

Building RAG pipelines typically requires several complex steps:

- Document ingestion
- Text preprocessing
- Document chunking
- Embedding generation
- Vector search setup
- Retrieval logic
- LLM orchestration
- User interface development

This process requires expertise across data engineering, machine learning, and application architecture and can take significant time to implement.

---

## Solution

The Auto-RAG Pipeline Generator simplifies this process by automating the RAG architecture within Snowflake using Cortex AI capabilities.

The pipeline performs the following tasks:

1. Store enterprise documents
2. Split documents into semantic chunks
3. Retrieve relevant chunks based on user queries
4. Generate responses using Snowflake Cortex LLM
5. Provide an interactive chat interface via Streamlit

---

## Architecture

Enterprise Documents  
↓  
Document Storage (Snowflake Table)  
↓  
Document Chunking  
↓  
Context Retrieval  
↓  
LLM Generation (AI_COMPLETE)  
↓  
Streamlit Chat Interface

---

## Implementation

### Document Ingestion

Enterprise documents are stored in a table called `DEMO_DOCUMENTS`.

Example:

| DOC_NAME | CONTENT |
|---------|---------|
| hr_policy | Employees receive 20 annual leave days |
| product_manual | SmartWatch X200 battery life is 48 hours |

---

### Document Chunking

Documents are split into smaller segments and stored in a table called `DOC_CHUNKS`.

Example:

| SOURCE_FILE | CHUNK_TEXT |
|-------------|------------|
| hr_policy | Employees receive 20 annual leave days |

---

### Retrieval

When a user asks a question, the system retrieves relevant chunks from the knowledge base and aggregates them into a context block.

---

### LLM Response Generation

The retrieved context and user question are passed to Snowflake Cortex using the `AI_COMPLETE()` function.

Example prompt:

Context:  
Employees receive 20 annual leave days.

Question:  
How many leave days do employees get?

Answer:  
Employees receive 20 annual leave days.

---

### Streamlit Interface

A Streamlit application inside Snowflake allows users to ask questions and receive AI-generated responses.

Example interaction:

User:  
What is the battery life of SmartWatch X200?

Response:  
The SmartWatch X200 has a battery life of 48 hours.

---

## Technologies Used

- Snowflake
- Snowflake Cortex AI
- Snowpark SQL
- Streamlit in Snowflake

---

## Future Improvements

- Automatic RAG pipeline generation using Cortex Code
- Semantic vector search
- Automatic document ingestion from stages
- Smart chunking strategies
- Automated pipeline updates using Streams and Tasks

---

## Conclusion

This project demonstrates how Snowflake Cortex can be used to build enterprise knowledge assistants using Retrieval-Augmented Generation.

The Auto-RAG Pipeline Generator concept simplifies the creation and maintenance of RAG pipelines within the Snowflake ecosystem.
