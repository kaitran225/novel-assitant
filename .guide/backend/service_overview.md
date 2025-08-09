# Backend Service Overview

## Main Services
- **FastAPI Server:** Handles all API requests, authentication, and orchestration.
- **Agent Orchestrator:** Manages agent tasks, context, and LLM communication.
- **File Scanner & Indexer:** Scans, chunks, and indexes all project files for agent use.
- **Ollama Integration:** Connects to local LLM runner for AI-powered features.

## Architecture
- Microservice-ready, but deploys as a monolith for local/SMB, or as separate services for enterprise.
- All services communicate via secure REST or gRPC.

## Enterprise Features
- Role-based access, audit logging, and compliance support.
- Scalable via Docker/Kubernetes.

---

For deployment, see `deployment.md`.
