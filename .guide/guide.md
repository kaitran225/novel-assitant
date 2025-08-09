## Novel Writing AI Agent Architecture

![AI Agent Architecture](../attachments/file/guide/ai_agent_architecture.png)

### Overview
This architecture adapts advanced agent design for a novel-writing assistant. The agent perceives user input, reasons about story context, plans creative actions, and interacts with both memory (lore, past writing) and the writing environment (files, editor).

### Intra-execution (Agent Internals)
- **Perception:**
	- Receives user prompts, file changes, or editor events.
	- Formats input and generates embeddings for semantic understanding.
- **Brain:**
	- **Reasoning:** Uses an LLM to break down user requests into subtasks (e.g., analyze character arc, check lore consistency, suggest plot twists).
	- **Planning:** Organizes subtasks into actionable steps (e.g., generate outline, propose dialogue, update character sheet).
	- Iterates between reasoning and planning for complex tasks.
- **Action:**
	- Executes planned actions: writes suggestions, edits files, updates metadata, or interacts with the user.

### Interaction (External Modules)
- **AI Agent:**
	- Can collaborate with other agents (e.g., a "lore checker" or "dialogue improver").
- **Memory:**
	- Stores and retrieves story context, character info, world lore, and past writing.
	- Uses vector search for relevant passages and facts.
- **Environment:**
	- The user's file system, editor, and any external tools or APIs.
	- The agent can read, write, and organize project files.

### Example Flow
1. User asks: "Suggest a plot twist for my main character."
2. Perception: Agent parses the request and retrieves relevant story context from memory.
3. Brain: LLM reasons about the character's arc, plans possible twists, and checks for lore consistency.
4. Action: Agent presents 2-3 plot twist options, optionally updates the outline or character sheet.
5. User selects a twist; agent helps generate the next scene or dialogue.

### Benefits
- Maintains world and character consistency.
- Adapts to user style and evolving story.
- Supports both reactive (on-demand) and proactive (suggests ideas) modes.
- Modular: new agent skills (e.g., theme tracker, canon validator) can be added easily.
# Novel Assistant App - Combined Guide

## Core Features

The app provides:

- A Markdown-based note editor for writing and organizing content.
- Folder and file organization for your projects.
- Graph view to visualize connections between notes and story elements.
- Bidirectional linking for easy navigation between related notes.
- Tagging and metadata to categorize and search your content.
- A plugin system to extend app functionality.
- A board feature (like Milaton) for visual story planning.
- Export/import options (Markdown, PDF, etc.) for your work.
- Cross-platform support (Windows, Mac, Linux).
- Linked blocks and block references (Notion-style) for flexible note structure.
- Advanced Markdown support (tables, embeds, code blocks, checklists).
- Inline and block-level linking for rich interconnections.
- Database/table view for managing notes or story elements.

## Graph Feature

Use the interactive graph view to visualize relationships between your notes, characters, and story elements. You can:

- Click nodes and edges to navigate between related items.
- Filter and highlight by tags, types, or relationships to focus on specific connections.
- Zoom, pan, and adjust layout for large graphs.
- Use contextual actions (create, edit, link) directly from the graph interface.

## IDE Agent & Project Indexing

The app includes an IDE Agent-like feature inspired by tools such as Cursor:

- Scans and indexes all files in your project (notes, character sheets, outlines, etc.).
- Builds a searchable index of your story universe, characters, and plot points.
- Uses the index to provide smart suggestions for storylines, plot development, and character arcs.
- Allows the AI to answer questions about your project, find inconsistencies, and suggest improvements.
- All indexing and analysis is performed locally for privacy and speed.

This feature helps you manage large projects, keep track of details, and get creative suggestions from the AI based on your entire project context.

## Tech Stack

### Frontend

- Flutter (for cross-platform desktop UI)
- Dart (main UI logic)

### Data Storage & Logic

- SQLite (for structured data storage, fast search, and relationships)
- Hive (for app logic, state management, and lightweight key-value storage)
- File system access for local file storage (notes, attachments, exports)

### Backend & Agent Orchestration

- FastAPI (Python, for local backend processes and AI integration)
- Project File Scanner & Indexer (Python): Scans and indexes all project files for agent use
- Agent Orchestrator (Python): Manages agent tasks, context, and communication with Ollama

---

## AI Agent: Conceptual Architecture & Workflow

### 1. Core Idea

Your AI agent becomes a personal story collaborator — aware of your past works, style, characters, lore, and unfinished plots.
When you give it a prompt, it:

- Reads your past writing (all files you have — novels, notes, outlines).
- Understands your style and narrative universe.
- Suggests storylines that align with existing canon or branch into new creative arcs.
- Can continuously learn from new writing you add.

### 2. High-Level Architecture

Think of it as a 5-layer system:

**Layer 1 — Data Ingestion**
Purpose: Load all user-written files into the AI’s knowledge base.
Data Types: .txt, .md, .docx, .pdf, .scriv, .json for outlines.

Steps:
	- File collector scans a “Story Repository” folder.
	- Extracts text content.
	- Splits large documents into semantic chunks (e.g., 500–1000 words) while keeping chapter/scene boundaries.
	- Tools: A document loader + text splitter.

**Layer 2 — Knowledge Index / Memory**
Purpose: Store and retrieve relevant context from your writing.
Approach:
	- Convert all chunks into embeddings (vector representation of meaning).
	- Store in a vector database (acts like a searchable “story memory”).
Why:
	- Lets the AI pull only relevant passages when you ask about a character, location, or plot.
	- Maintains your voice & style consistency.
	- Tools: FAISS, Pinecone, Weaviate, ChromaDB.

**Layer 3 — Reasoning Engine**
Purpose: The “brain” that decides what to suggest.
Capabilities:
	- Search memory for related story elements.
	- Understand narrative structure (Setup → Conflict → Resolution).
	- Suggest plotlines that fit your tone & pacing.
	- Optionally: Maintain character arcs, themes, and world rules.
Agent Style:
	- Could be a reactive agent (answers on demand) or proactive agent (suggests periodically).
	- Can chain tools: Retrieval → Analysis → Generation.

**Layer 4 — Generation**
Purpose: Produce storyline suggestions or continuations.
Approach:
	- Combine retrieved context from Layer 2 with your request.
	- Use an LLM (large language model) tuned for creative writing.
	- Apply style-preserving prompts (train or fine-tune with your text).
Output Types:
	- High-level story arcs.
	- Scene outlines.
	- Alternative endings.
	- Dialogue suggestions.

**Layer 5 — Interaction**
Purpose: How the writer communicates with the agent.
Modes:
	- Chat interface (ask “What’s a good next twist for Chapter 7?”).
	- In-editor assistant (VSCode, Obsidian, Scrivener plugin).
	- Standalone dashboard for browsing characters, locations, and arcs.
Extra Feature:
	- “Lore Book” view — dynamically generated summaries of characters, locations, and past events.

### 3. Example Workflow
User: Drops all novel files into the “Story Vault” folder.
Agent: Scans, chunks, and indexes them in memory.
User: Asks — “Give me three possible plot twists for the main character without breaking the lore.”
Agent:
	- Searches for all appearances of the character.
	- Understands their traits, past events, and unresolved threads.
	- Generates 3 possible twists consistent with your style.
User: Picks one and starts writing, optionally asking the AI to “fill in” scene details.

### 4. Key Concepts for Novel AI Agents
- Vector Retrieval = AI memory of your writing.
- Context-Aware Generation = Suggestions based only on your world’s rules.
- Style Transfer / Fine-tuning = Makes the AI write like you.
- World Consistency Checking = Prevents plot holes.
- Progressive Learning = AI keeps updating as you write more.

### 5. Possible Future Enhancements
- Character Relationship Graph — visual map of how characters connect.
- Theme Tracker — ensures themes like “betrayal” or “hope” stay coherent.
- Storyline Probability Engine — scores ideas based on pacing and tension.
- Cross-File Canon Validator — flags contradictions in lore.

### AI Integration

- Ollama (local LLM runner for AI-powered suggestions and agent reasoning)

## Getting Started

### Ollama Installation & Setup

To use AI features in this app, you must install Ollama (the local AI engine) separately:

1. Download Ollama from the official website: https://ollama.com/download
2. Follow the installation instructions for your operating system (Windows, Mac, or Linux).
3. After installation, launch Ollama. It will run as a background service on your computer.
4. Download and set up your preferred AI model (e.g., Llama, Mistral) using the Ollama interface or command line.
5. Ensure Ollama is running before starting the Novel Assistant app. The app will connect to Ollama’s local API (usually http://localhost:11434) to provide AI-powered features.

If Ollama is not running, AI features will be unavailable. For troubleshooting, see the Ollama documentation or check that the service is active.

1. Set up the Flutter app scaffold for desktop (Windows, Mac, Linux).
2. Implement the Markdown editor for writing using Flutter widgets.
3. Add file and folder navigation for organization.
4. Build the board feature for story planning.
5. Add the graph view for note relationships.
6. Create the plugin API for extensibility (using Dart/Flutter).
7. Polish the UI/UX for a smooth experience.
8. Test thoroughly and write documentation.
