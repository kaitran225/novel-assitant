# Indexing Strategy

The agent uses a robust, enterprise-grade indexing strategy to ensure fast, context-rich access to all project data:

## File Scanning & Ingestion

- Recursively scans all project folders for supported file types (.md, .txt, .docx, .json, etc.).
- Extracts text, metadata, and structure (chapters, scenes, characters).
- Supports incremental indexing (only changed files are re-indexed).

## Chunking & Embedding

- Splits large documents into semantic chunks (e.g., scenes, paragraphs, or 500–1000 word blocks).
- Generates vector embeddings for each chunk using state-of-the-art models.

## Vector Database

- Stores all embeddings in a high-performance vector database (e.g., FAISS, ChromaDB, Pinecone for cloud).
- Enables semantic search, similarity queries, and context retrieval.

## Metadata & Relationships

- Indexes relationships between notes, characters, locations, and plot points.
- Maintains a graph of interlinked story elements for advanced queries.

## Real-Time Updates

- Watches for file changes and updates the index in real time.
- Supports manual re-indexing and scheduled background indexing.

## Security & Compliance

- Indexing respects user roles and permissions.
- All indexing operations are logged for auditability.

For more, see `agent_capabilities.md` and `ollama_integration.md`.
