# QA Pipeline Structure

```
qa-pipeline/
├── query_analysis/          # Analyze user question and convert to embedding vector
├── document_retrieval/      # Retrieve relevant documents using vector similarity (Milvus)
├── context_assembly/        # Combine question and documents to build prompt
└── answer_generation/       # Generate answer using AWS Bedrock LLM
```
