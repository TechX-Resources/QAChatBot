# QAChatBot

## Problem Statement

As enterprise documentation platforms like Confluence and Notion grow, teams face severe information overload. Traditional keyword-based search fails to capture contextual meaning, resulting in inefficient information retrieval, repeated questions, and delayed workflows. Teams also struggle with navigating different formats and scattered knowledge across multiple tools.
A solution is needed to provide accurate, transparent, and context-aware answers from internal documents—seamlessly integrated into daily workflows.

---

## Project Idea

We propose building a Retrieval-Augmented Generation(RAG) based document QA chatbot that integrates with Notion, Confluence, and Slack. The system enables employees to ask natural language questions and receive precise answers based on internal documentation—enhanced with source citations and trust indicators. The architecture is modular, cloud-native, and optimized for enterprise deployment.

---

## System Overview (Pipeline)

1. Ingestion Layer (AWS EC2, AWS CLI)
   The system collects internal documents from Notion and Confluence using their official APIs. It supports scheduled synchronization and change detection to ensure document freshness. This ingestion process runs on virtual infrastructure with CLI authentication.

2. Preprocessing (Amazon S3 – optional for intermediate storage)
   The system cleans and normalizes text (e.g., HTML/Markdown tag removal, whitespace cleanup), segments it into semantic chunks (paragraphs, sections), and assigns metadata such as source, title path, and update time.

3. Embedding & Vector Storage (AWS Bedrock – Titan, AWS EC2 for hosting Milvus)
   Each text chunk is embedded into a dense vector using Titan Embedding from AWS Bedrock. These vectors and metadata are stored in Milvus, a scalable vector database.

4. Query & Retrieval Pipeline (AWS Bedrock – Titan)
   User queries are embedded via AWS Bedrock, classified by type, and routed to the correct document collection. Relevant document chunks are retrieved from Milvus using vector similarity search.

5. Prompt Construction & LLM Response (AWS Bedrock – Claude or Jurassic)
   The system constructs a prompt using the user query and retrieved document chunks, which is then sent to a large language model to generate an answer. The response includes inline citations and document trust scores.

6. Output Interface (AWS EC2)
   Responses are delivered through a FastAPI backend and a Slack bot. The API also supports external integration. All backend services are deployed on scalable cloud infrastructure.
