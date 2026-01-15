# Dev Consultant Plugin

Web application development consulting plugin for Claude Code with specialized agents for requirements gathering, UI/UX design, technical specification, and project planning.

## Overview

Dev Consultant transforms vague customer requirements into detailed, actionable specifications for web applications. It orchestrates 7 specialized agents through a structured workflow, producing comprehensive documentation from initial concept to development roadmap.

Perfect for planning **HTML + Tailwind CSS + vanilla JavaScript** web applications with client-side storage (LocalStorage + IndexedDB).

## Plugin Structure

```
dev-consultant/
├── .claude-plugin/
│   └── plugin.json           # Plugin configuration
├── agents/
│   ├── interviewer.md        # Requirements extraction
│   ├── ui-sketcher.md        # ASCII wireframe generation
│   ├── documentation-writer.md # Technical specifications
│   ├── tech-researcher.md    # Data architecture design
│   ├── mermaid-designer.md   # Flow diagram creation
│   ├── interactive-designer.md # Animation specifications
│   └── planner.md            # Project roadmap planning
├── skills/
│   └── webapp-consultant/
│       ├── SKILL.md          # Main skill definition
│       ├── references/       # Reference materials
│       │   ├── workflow.md
│       │   ├── interview-patterns.md
│       │   ├── ascii-art-guide.md
│       │   ├── localbase-guide.md
│       │   ├── ux-philosophy.md
│       │   ├── mermaid-patterns.md
│       │   ├── tailwind-animations.md
│       │   └── planning-methods.md
│       └── assets/
│           └── planning-template.md
├── LICENSE
└── README.md
```

## 7 Specialized Agents

### 1. **Interviewer**
Extracts clear requirements from vague customer input through persistent questioning.

**Triggers**: Vague requirements, unclear scope, undefined user personas

**Output**: Requirements document with problem statement, target users, must-have features, constraints

### 2. **UI Sketcher**
Generates ASCII wireframes showing layout and UI components.

**Triggers**: "Show me the layout", feature description needs visual representation

**Output**: ASCII wireframes with Tailwind class hints and UX annotations

### 3. **Documentation Writer**
Creates comprehensive technical specifications with UX philosophy integration.

**Triggers**: Wireframes complete, need detailed documentation

**Output**: Markdown spec with user stories, UX analysis (Norman/Nielsen principles), acceptance criteria

### 4. **Tech Researcher**
Designs data architecture and storage patterns for client-side applications.

**Triggers**: Data storage questions, repository pattern needs

**Output**: Technical architecture with localbase collections, repository classes, code examples

### 5. **Mermaid Designer**
Creates flowcharts and diagrams using Mermaid.js with semantic coloring.

**Triggers**: "Show me the flow", process needs visualization

**Output**: Mermaid diagrams for user flows, CRUD operations, state transitions

### 6. **Interactive Designer**
Specifies Tailwind animations and micro-interactions.

**Triggers**: Animation needs, interaction design specification

**Output**: Animation specs with Tailwind code for buttons, cards, modals, loading states

### 7. **Planner**
Creates prioritized development roadmaps with MoSCoW/RICE/Kano frameworks.

**Triggers**: "What should we build first?", prioritization needed

**Output**: Project roadmap with phase breakdown, WBS, critical path, milestones

## Agent Workflow

```
Customer Request (vague)
         ↓
   Interviewer ← Persistent questioning
         ↓
   UI Sketcher → ASCII wireframes
         ↓
   Documentation Writer → Markdown spec with UX philosophy
         ↓
  ┌──────┴──────┬──────────────┐
  ↓             ↓              ↓
Tech Researcher  Mermaid       Interactive
  (Data)         Designer      Designer
                 (Flows)       (Animations)
  └──────┬──────┴──────────────┘
         ↓
      Planner → Final roadmap
         ↓
   Complete Specification
```

## Skills

### webapp-consultant

Main consulting skill that orchestrates all agents to transform vague requirements into detailed specifications.

**Use when**:
- Customer describes requirements vaguely ("I want something like...")
- Planning HTML + Tailwind + vanilla JS web apps
- Creating comprehensive project documentation
- Generating technical specifications without backend
- Creating project roadmaps with prioritization

**Tech Stack**:
- Frontend: HTML + Tailwind CSS + vanilla JavaScript
- Storage: LocalStorage (settings) + IndexedDB via localbase (data)
- No backend required

**Example**:
```
User: "I need a tool to manage my tasks"

Assistant invokes webapp-consultant skill:
1. Interviewer clarifies requirements
2. UI Sketcher creates wireframes
3. Documentation Writer creates spec
4. Tech Researcher designs data model
5. Mermaid Designer creates flows
6. Interactive Designer adds animations
7. Planner creates roadmap

Output: Complete 20-page specification ready for development
```

## Installation

1. Clone this repository to your Claude Code plugins directory:
```bash
/plugin marketplace add Mineru98/dev-consultant
/plugin install dev-consultant
```

2. The plugin will be automatically detected by Claude Code on next startup.

## Usage

### Using Agents Directly

```
Use the Task tool with subagent_type parameter:

Example:
Task(
  subagent_type="interviewer",
  prompt="Extract requirements for a personal finance tracker",
  description="Gather requirements"
)
```

### Using the webapp-consultant Skill

```
Invoke the skill when planning a new web application:

User: "Help me plan a todo list app"

Claude automatically:
1. Runs interviewer to clarify requirements
2. Creates wireframes with ui-sketcher
3. Writes specification with documentation-writer
4. Designs data architecture with tech-researcher
5. Creates flow diagrams with mermaid-designer
6. Specifies animations with interactive-designer
7. Generates roadmap with planner
```

## Features

### Requirements Gathering
- Persistent questioning patterns
- Structured interview framework
- Confirmation and validation
- Problem statement extraction
- User persona definition

### Visual Design
- ASCII wireframe generation
- Tailwind CSS class hints
- Responsive design notes
- UX principle annotations (Norman, Nielsen)
- Interaction state documentation

### Technical Specification
- User stories with acceptance criteria
- UX philosophy integration
- Data model design (localbase)
- Repository pattern implementation
- LocalStorage + IndexedDB strategy

### Flow Documentation
- Mermaid.js diagrams
- Semantic color coding (ai-diagrams-toolkit)
- User flow visualization
- CRUD operation flows
- Error handling paths
- State machine diagrams

### Animation Design
- Tailwind animation specifications
- Hover/focus/active states
- Loading indicators
- Modal/toast animations
- Micro-interactions
- Accessibility (reduced motion)

### Project Planning
- MoSCoW prioritization
- RICE scoring (optional)
- Kano model (optional)
- Phase breakdown with deliverables
- Work breakdown structure (WBS)
- Critical path analysis
- Milestone definitions

## Tech Stack Support

This plugin specializes in client-side web applications:

### Frontend
- HTML5
- Tailwind CSS
- Vanilla JavaScript (ES6+)

### Storage
- **LocalStorage**: User settings and preferences
- **IndexedDB via localbase**: Application data

### Constraints
- No backend/server required
- No file system API
- Browser storage only (50MB typical limit)
- Desktop-first, responsive design

## Output

Complete Markdown specification containing:

1. Executive summary
2. Requirements document
3. ASCII wireframes
4. Technical specification
5. Data architecture
6. User flow diagrams (Mermaid)
7. Animation specifications
8. Development roadmap
9. Work breakdown structure
10. Milestones and success criteria

## When to Use

✅ **Use dev-consultant when**:
- Customer has vague or unclear requirements
- Planning a new web app from scratch
- Need comprehensive documentation before coding
- Want structured requirements gathering
- Building HTML + Tailwind + vanilla JS app
- Client-side only (no backend)

❌ **Don't use when**:
- Requirements are crystal clear
- Building backend/server-side application
- Need React/Vue/framework-specific planning
- Just need quick prototype

## Examples

### Example 1: Task Manager

**Input**: "I need a tool to manage my tasks"

**Process**:
1. Interviewer clarifies: Personal or team? Categories? Deadlines?
2. UI Sketcher creates: Task list, add form, filter sidebar
3. Documentation Writer: User stories, acceptance criteria
4. Tech Researcher: Task collection, TaskRepository
5. Mermaid Designer: CRUD flows, filtering logic
6. Interactive Designer: Hover states, loading spinners
7. Planner: Phase 1 (CRUD), Phase 2 (filters), Phase 3 (polish)

**Output**: 20-page specification ready for implementation

### Example 2: Note Taking App

**Input**: "Something like Evernote but simpler"

**Process**:
1. Interviewer: Which Evernote features? Rich text? Tags?
2. UI Sketcher: Note list, editor, sidebar
3. Documentation Writer: Editing UX, tag system spec
4. Tech Researcher: Note collection, Tag collection
5. Mermaid Designer: Note creation flow, tag management
6. Interactive Designer: Editor interactions, tag animations
7. Planner: MVP (basic notes) → Enhanced (tags, search)

**Output**: Complete specification with realistic timeline

## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

See [LICENSE](LICENSE) file for details.

## Support

For issues, questions, or feature requests, please open an issue on GitHub.

## Credits

Created for Claude Code plugin ecosystem.

**Reference Materials**:
- Norman, Don. "The Design of Everyday Things"
- Nielsen, Jakob. "Usability Heuristics"
- ai-diagrams-toolkit (Mermaid patterns)
- localbase (IndexedDB wrapper)

## Version

Current version: 1.0.0