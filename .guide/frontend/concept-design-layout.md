# Concept Design Layout for Novel Assistant App

## 1. App Structure Overview

- **Header**: Logo, app name, theme switcher, user profile/avatar
- **Sidebar (optional for desktop)**: Navigation links (Dashboard, Projects, Characters, Plot, Settings)
- **Main Content Area**: Dynamic, changes based on selected section
- **Footer**: Copyright, version, quick links

---

## 2. Main Screens

### Dashboard

- Quick stats (word count, recent activity)
- Shortcuts to recent projects
- Inspiration/quote of the day

### Project Workspace

- **Project List**: Sidebar or modal for switching between projects
- **Editor Area**: Rich text editor for writing
- **Outline/Chapters**: Collapsible panel for chapter/scene navigation
- **Notes/References**: Side panel or modal for quick notes

### Character Management

- List of characters with avatars
- Detail view: name, description, traits, relationships
- Add/edit/delete character

### Plot/Timeline

- Visual timeline or board for plotting events
- Drag-and-drop for rearranging scenes/chapters
- Color-coded for arcs/threads

### Settings

- Theme selection (dark/light)
- Font and layout preferences
- Export/import options

---

## 3. UI Components

- **Buttons**: Primary, secondary, icon buttons
- **Cards**: For project/character summaries
- **Modals**: For add/edit actions
- **Tabs**: For switching between sections (e.g., notes, outline)
- **Tooltips**: For extra info/help
- **Notifications**: Toasts for actions (save, error, etc.)

---

## 4. Responsive Design

- **Desktop**: Sidebar navigation, multi-panel layout
- **Tablet**: Collapsible sidebar, stacked panels
- **Mobile**: Bottom navigation, single-column layout, modals for details

---

## 5. Color & Theme Usage

- Use the provided color palette and theme variables
- Maintain high contrast and accessibility
- Accent colors for highlights and actions

---

## 6. Example Wireframe (Text)

+------------------------------------------------------+
| Header: Logo | App Name | Theme | Profile            |
+-------------------+----------------------------------+
| Sidebar           | Main Content Area                |
| - Dashboard       | - Section Title                  |
| - Projects        | - Main editor/cards/lists        |
| - Characters      |                                  |
| - Plot/Timeline   |                                  |
| - Settings        |                                  |
+-------------------+----------------------------------+
| Footer: Copyright | Version | Links                  |
+------------------------------------------------------+

---

> For visual mockups, use Figma or similar tools to translate this structure into UI screens.
