# Data Flow

## Enterprise Data Flow Overview

1. **User Interaction:**
	- User interacts with the Flutter desktop client UI.
2. **Frontend Logic:**
	- Dart/Flutter handles UI state, local caching (Hive), and input validation.
3. **API Requests:**
	- Secure HTTPS requests (with JWT) sent to FastAPI backend.
4. **Backend Processing:**
	- FastAPI routes requests to agent orchestrator, AI (Ollama), or storage.
5. **AI/Agent:**
	- Agent orchestrator manages context, persona, and LLM calls (Ollama).
6. **Data Storage:**
	- Hive for app state/config, SQLite for structured/relational data.
7. **Response:**
	- Backend returns results to frontend, which updates UI.

> All data flows are logged and auditable for enterprise compliance.
