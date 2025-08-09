# Project: Novel Assistant

## Description
A desktop application for story writing, inspired by Obsidian, with markdown support, note traversal (linked list), and AI assistant integration. Built with C# and WPF.

## Features
- Markdown-based note system
- Linked list traversal for notes (next/previous)
- AI assistant integration (expandable)
- User-friendly UI

## Project Structure
- /NovelAssistant/         # Main app source code
- /NovelAssistant/Notes/   # Note management (markdown, linked list)
- /NovelAssistant/AI/      # AI assistant integration
- /NovelAssistant/Utils/   # Utilities
- /docs/                   # Documentation
- README.md                # Project overview
- .gitignore               # Git ignore rules

## TODO List
- [ ] Scaffold WPF project
- [ ] Implement markdown note system
- [ ] Add linked list traversal for notes
- [ ] Integrate AI assistant (API)
- [ ] Design modern UI
- [ ] Write documentation

## API List (Expandable)
- AI Assistant API (OpenAI, local LLM, etc.)
- File system API for notes
- Markdown rendering API

## .NET Tech Stack (Compact)
- .NET 8.0 (or latest LTS)
- WPF for UI
- C# 12+
- Markdig (NuGet) for markdown parsing
- Newtonsoft.Json (NuGet) for JSON
- MVVM pattern (recommended)

---
See README.md for more details.
