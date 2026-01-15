---
name: webapp-consultant
description: Web application development consulting skill for transforming vague requirements into detailed specifications. Use when (1) customers describe requirements vaguely ("I want something like..."), (2) planning HTML + Tailwind + vanilla JS web apps, (3) creating comprehensive project documentation, (4) generating technical specifications without backend, (5) creating project roadmaps with prioritization. Triggers include phrases like "make me an app", "build a web app", "I need a tool for...", or any unclear feature requests that need clarification.
---

# Web App Development Consultant

A comprehensive consulting system that transforms vague customer requirements into detailed specifications for desktop web apps using **HTML + Tailwind CSS + vanilla JavaScript** with **no backend** (LocalStorage + IndexedDB only).

## Overview

This skill orchestrates 7 specialized agents to create complete project specifications, from initial requirements gathering through final development roadmap. Perfect for turning ambiguous customer requests into actionable development plans.

## Quick Start

When a customer describes what they want to build in vague terms, invoke this skill to guide them through a structured planning process that produces:

1. Clarified requirements document
2. Visual ASCII wireframes
3. Comprehensive technical specification
4. Data architecture design
5. User flow diagrams
6. Animation specifications
7. Prioritized development roadmap

## Agent Workflow

```
Customer Request (vague)
         ↓
   [Interviewer] ← Persistent questioning until requirements clear
         ↓
   [UI Sketcher] → ASCII wireframes with Tailwind hints
         ↓
   [Documentation Writer] → Markdown spec with UX philosophy (Norman/Nielsen)
         ↓
   [Tech Researcher] → localbase patterns, repository architecture
         ↓
   [Mermaid Designer] → Flowcharts (ai-diagrams-toolkit style)
         ↓
   [Interactive Designer] → Tailwind animations, micro-interactions
         ↓
   [Planner] → MoSCoW/RICE priorities, WBS, phases
         ↓
   Final Output: Complete Markdown specification
```

## 7 Specialized Agents

### 1. Interviewer
**Role**: Extract requirements through persistent questioning

**Use When**:
- Customer describes features vaguely
- Requirements are unclear or ambiguous
- Scope needs clarification
- User personas are undefined

**Output**: Requirements document with problem statement, target users, must-have features, constraints, and success criteria

---

### 2. UI Sketcher
**Role**: Generate ASCII wireframes

**Use When**:
- Requirements need visual representation
- Customer asks "show me what it looks like"
- Layout structure needs definition
- Discussing screen organization

**Output**: ASCII wireframes for each screen with Tailwind class hints and UX annotations

---

### 3. Documentation Writer
**Role**: Create technical specifications with UX philosophy

**Use When**:
- Wireframes need detailed documentation
- UX decisions need philosophical explanation
- Creating comprehensive project specs
- Writing user stories and acceptance criteria

**Output**: Markdown specification with user stories, UX analysis connecting to Norman/Nielsen principles, design system, and success metrics

---

### 4. Tech Researcher
**Role**: Research client-side technology patterns

**Use When**:
- Defining data storage strategy
- Designing localbase collections
- Implementing repository pattern
- Researching client-side alternatives

**Output**: Technical architecture document with data model, repository classes, LocalStorage/IndexedDB strategy, and code examples

---

### 5. Mermaid Designer
**Role**: Create flowcharts using Mermaid.js

**Use When**:
- Visualizing user flows
- Creating process diagrams
- Documenting system architecture
- Showing state transitions

**Output**: Mermaid diagrams with semantic coloring for all major user flows and processes

---

### 6. Interactive Designer
**Role**: Design Tailwind animations and micro-interactions

**Use When**:
- Defining hover/focus/active states
- Designing loading animations
- Specifying transitions
- Creating micro-interactions

**Output**: Animation specification with Tailwind code for buttons, cards, inputs, modals, toasts, and loading states

---

### 7. Planner
**Role**: Structure phases, priorities, and development roadmap

**Use When**:
- Creating development roadmaps
- Prioritizing features with MoSCoW/RICE/Kano
- Breaking down work into phases
- Identifying dependencies
- Determining development order

**Output**: Project roadmap with MoSCoW prioritization, phase breakdown, WBS, critical path analysis, and milestones

## Agent Delegation

When using the Task tool to delegate to agents, follow this pattern:

```
TASK: [Specific atomic goal]
EXPECTED OUTCOME: [Concrete deliverables]
REQUIRED AGENT: [Agent name from plugin]
CONTEXT: [File paths, patterns, constraints]

MUST DO:
- [Exhaustive requirement 1]
- [Exhaustive requirement 2]

MUST NOT DO:
- [Forbidden action 1]
- [Forbidden action 2]
```

### Delegation Sequence

**Sequential (must be in order)**:
1. Interviewer → UI Sketcher → Documentation Writer

**Parallel (can run simultaneously)**:
- After Documentation Writer completes:
  - Tech Researcher
  - Mermaid Designer
  - Interactive Designer

**Final (needs all previous outputs)**:
- Planner (assembles everything into roadmap)

## Tech Stack Constraints

This skill targets **desktop web apps** with:

- **Frontend**: HTML + Tailwind CSS + vanilla JavaScript (ES6+)
- **Storage**: LocalStorage (settings) + IndexedDB via localbase (data)
- **No Backend**: All logic runs client-side
- **No File System API**: Browser storage only
- **Desktop-First**: Responsive design for tablet/mobile

## Reference Materials

Load based on current task:

| Task | Reference |
|------|-----------|
| Overall process | `references/workflow.md` |
| Customer interviews | `references/interview-patterns.md` |
| ASCII wireframes | `references/ascii-art-guide.md` |
| Data persistence | `references/localbase-guide.md` |
| UX documentation | `references/ux-philosophy.md` |
| Flowcharts | `references/mermaid-patterns.md` |
| Animations | `references/tailwind-animations.md` |
| Prioritization | `references/planning-methods.md` |

## Output Format

Final deliverable is a **comprehensive Markdown file** containing:

1. **Executive Summary**
   - Project overview and goals
   - Target users and personas

2. **Requirements**
   - Problem statement
   - Must-have features
   - Should-have features
   - Could-have features
   - Constraints

3. **Wireframes**
   - ASCII wireframes for all screens
   - UX annotations
   - Responsive behavior notes

4. **Technical Specification**
   - Data model (localbase collections)
   - Repository pattern implementation
   - Storage strategy

5. **User Flows**
   - Mermaid diagrams for all major flows
   - Error handling paths
   - State transitions

6. **Animation Specifications**
   - Tailwind code for all interactions
   - Hover, focus, active states
   - Loading indicators
   - Modal/toast animations

7. **Development Roadmap**
   - MoSCoW prioritization
   - Phase breakdown with deliverables
   - Work breakdown structure (WBS)
   - Critical path analysis
   - Milestones with criteria

See `assets/planning-template.md` for the complete template.

## Example Usage

### Scenario 1: Vague Request

**Customer**: "I need a tool to manage my tasks"

**Action**: Invoke webapp-consultant skill

**Process**:
1. Interviewer asks questions to clarify requirements
2. UI Sketcher creates wireframes for task list, add form, filters
3. Documentation Writer creates spec with user stories
4. Tech Researcher designs Task collection and TaskRepository
5. Mermaid Designer creates CRUD and filtering flows
6. Interactive Designer specifies animations for task interactions
7. Planner creates roadmap with Must-Have (CRUD) and Should-Have (filters, search)

**Output**: 20-page Markdown specification ready for development

### Scenario 2: Feature-Rich App

**Customer**: "Something like Trello but simpler, for personal use"

**Action**: Invoke webapp-consultant skill

**Process**:
1. Interviewer explores what features from Trello are needed
2. UI Sketcher creates board/card/list wireframes
3. Documentation Writer documents drag-and-drop UX philosophy
4. Tech Researcher designs Board, List, Card collections
5. Mermaid Designer creates board management flows
6. Interactive Designer specifies drag-and-drop animations
7. Planner creates phased roadmap (Phase 1: Basic CRUD, Phase 2: Drag-drop, Phase 3: Polish)

**Output**: Complete specification with realistic implementation plan

## When to Use This Skill

✅ **Use when**:
- Customer request is vague or unclear
- Planning a new web app from scratch
- Need comprehensive documentation before coding
- Want structured approach to requirements gathering
- Building HTML + Tailwind + vanilla JS app
- No backend/database available (client-side only)

❌ **Don't use when**:
- Requirements are already crystal clear
- Building backend/server-side application
- Need React/Vue/framework-specific planning
- Just need quick prototype without documentation

## Success Criteria

A successful consultation produces:

- ✅ Clarified requirements with customer validation
- ✅ Visual wireframes showing all screens
- ✅ Technical specification with code examples
- ✅ Complete data architecture
- ✅ Flow diagrams for major features
- ✅ Animation specifications with Tailwind code
- ✅ Prioritized roadmap with realistic phases
- ✅ Ready for immediate development start

## Tips for Effective Use

1. **Let the interviewer do its job**: Don't rush the questioning phase. Clear requirements save development time.

2. **Review wireframes early**: Visual representation helps catch missing features before detailed documentation.

3. **Validate UX philosophy**: Documentation Writer connects designs to established principles - ensure these align with user needs.

4. **Keep tech stack simple**: This skill optimizes for vanilla JS. Don't try to force frameworks.

5. **Trust the prioritization**: MoSCoW method ensures MVP scope is realistic.

6. **Use the full workflow**: Skipping agents leads to incomplete specifications.

## Support

This skill creates specifications for development, not implementations. After the specification is complete, you'll need to:

1. Set up project structure (HTML, Tailwind config, JS modules)
2. Implement repository classes
3. Build UI components
4. Connect UI to data layer
5. Add animations and interactions
6. Test and deploy

For implementation guidance, refer to the technical specification created by this skill.
