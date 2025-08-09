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
