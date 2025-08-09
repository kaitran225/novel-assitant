# Project File Scanner & Indexer

- **Category:** Backend/Agent
- **Version:** Custom
- **Website/Docs:** N/A (custom Python module)
- **Why Chosen:** Enables agent to scan and index all user project files for context-aware suggestions.
- **Key Features:** File scanning, text extraction, chunking, semantic splitting.
- **Integration Points:** FastAPI backend, vector database.
- **Alternatives Considered:** None (custom logic required)
- **Risks/Limitations:** Must handle many file types, performance on large projects.
- **Best Practices:** Use efficient file IO, support common formats, log errors.
