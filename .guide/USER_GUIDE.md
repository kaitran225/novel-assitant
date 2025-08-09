# User Guide for Novel Assistant (100x Detailed)

Welcome to the Novel Assistant! This guide will walk you through every feature, workflow, and tip for using the app to its fullest potential. Whether you’re a beginner or a power user, you’ll find step-by-step instructions, troubleshooting, and best practices here.

---

## Table of Contents
1. Introduction
2. Installation & Setup
3. Creating and Managing Notes
4. Markdown Writing Tips
5. Navigating Notes (Linked List System)
6. Using the AI Assistant (Ollama)
7. Organizing Your Story
8. Exporting and Backing Up Work
9. Customizing the App
10. Troubleshooting & FAQ
11. Advanced Features
12. Keyboard Shortcuts
13. Privacy & Offline Usage
14. Getting Help

---

## 1. Introduction
Novel Assistant is a desktop app for story writers, inspired by Obsidian, with:
- Markdown-based notes
- Linked list navigation (next/previous)
- Offline AI assistant (Ollama)
- User-friendly, modern UI

## 2. Installation & Setup
- Ensure .NET 9 SDK is installed
- Download and install the app (see SETUP_GUIDE.md)
- On first launch, the app will auto-detect your system and suggest the best AI model
- Ollama will be downloaded and set up automatically if not present

## 3. Creating and Managing Notes
- Click “New Note” to create a markdown file
- Notes are saved in the /Notes/ directory
- Use folders and tags for organization
- Rename, delete, or move notes via right-click menu

## 4. Markdown Writing Tips
- Use # for headings, **bold**, *italic*, and [links](url)
- Insert images: ![alt text](path/to/image.png)
- Use code blocks for formatting
- See the Markdown Cheat Sheet in the Help menu

## 5. Navigating Notes (Linked List System)
- Each note is part of a linked list for easy traversal
- Use “Next” and “Previous” buttons to move between notes
- The app remembers your last position in the list
- You can reorder notes in the navigation panel

## 6. Using the AI Assistant (Ollama)
- Click the AI Assistant icon or press Ctrl+Space
- Ask for brainstorming, plot suggestions, or editing help
- The AI runs 100% offline for privacy
- The app will suggest the best model based on your hardware (RAM, CPU)
- You can switch models in Settings
- All AI prompts and responses are stored locally

## 7. Organizing Your Story
- Use folders for chapters, characters, worldbuilding, etc.
- Tag notes with #character, #plot, #setting, etc.
- Use backlinks ([[note name]]) to connect ideas
- The graph view shows relationships between notes

## 8. Exporting and Backing Up Work
- Export notes as PDF, DOCX, or plain text
- Backup your entire vault with one click
- Automatic backups can be enabled in Settings

## 9. Customizing the App
- Choose from light/dark themes
- Adjust font size and editor layout
- Configure keyboard shortcuts
- Add custom CSS for advanced theming

## 10. Troubleshooting & FAQ
- See the Troubleshooting section in SETUP_GUIDE.md
- Common issues: AI not responding, notes not saving, UI glitches
- Restart the app or check logs in /Logs/
- For AI issues, ensure Ollama is running and the model is downloaded

## 11. Advanced Features
- Use the command palette (Ctrl+P) for quick actions
- Enable experimental features in Settings
- Integrate with external editors (e.g., VS Code)

## 12. Keyboard Shortcuts
- Ctrl+N: New note
- Ctrl+S: Save note
- Ctrl+P: Command palette
- Ctrl+Space: AI Assistant
- Ctrl+Tab: Next note
- Ctrl+Shift+Tab: Previous note
- F1: Help

## 13. Privacy & Offline Usage
- All data and AI processing stay on your device
- No internet connection required after setup
- You control all your notes and AI data

## 14. Getting Help
- Access in-app help via the Help menu
- Read SETUP_GUIDE.md, AI_GUIDE.md, and DEVELOPER_GUIDE.md for more
- Join the community (links in README.md)

---

For more details, see the other guides in this project. Happy writing!
