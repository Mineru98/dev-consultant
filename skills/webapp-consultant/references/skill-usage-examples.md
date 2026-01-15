# Skill Usage Examples

Practical examples of webapp-consultant skill usage.

## Example 1: Task Manager App

### Customer Request
> "I need a tool to manage my tasks"

### Process

**Phase 1: Interviewer**
- Clarifies: Personal or team use?
- Identifies: Task attributes (title, due date, priority)
- Confirms: Filtering, search, completion tracking needed

**Phase 2: UI Sketcher**
- Creates wireframes: Task list, add form, filter bar
- Notes: Card-based layout, checkbox completion

**Phase 3: UX Spec Writer**
- Documents: User stories for CRUD operations
- Applies: Nielsen's visibility heuristic for task status

**Phase 4: Client Tech Architect**
- Designs: Task collection schema
- Implements: TaskRepository with filter methods

**Phase 5: Mermaid Designer**
- Maps: Add/Edit/Delete task flows
- Documents: Filter state transitions

**Phase 6: Interactive Designer**
- Specifies: Checkbox toggle animation
- Designs: Card hover effects

**Phase 7: Planner**
- Prioritizes: MVP (CRUD) → Phase 2 (filters) → Phase 3 (due dates)

**Phase 8: Browser QA**
- Tests: All CRUD operations
- Verifies: Data persistence

### Output
20-page specification ready for development

---

## Example 2: Kanban Board

### Customer Request
> "Something like Trello but simpler, for personal use"

### Process

**Phase 1: Interviewer**
- Explores: Which Trello features needed?
- Identifies: Boards, lists, cards, drag-and-drop
- Excludes: Team features, integrations

**Phase 2: UI Sketcher**
- Creates: Board view with columns
- Notes: Card drag handles, add card buttons

**Phase 3: UX Spec Writer**
- Documents: Drag-and-drop UX principles
- Specifies: Visual feedback during drag

**Phase 4: Client Tech Architect**
- Designs: Board, List, Card collections
- Implements: Position/ordering logic

**Phase 5: Mermaid Designer**
- Maps: Card movement between lists
- Documents: Board creation flow

**Phase 6: Interactive Designer**
- Specifies: Drag ghost styling
- Designs: Drop zone highlighting

**Phase 7: Planner**
- Phase 1: Basic CRUD
- Phase 2: Drag-and-drop
- Phase 3: Polish and animations

**Phase 8: Browser QA**
- Tests: Drag-and-drop across lists
- Verifies: Card ordering persistence

---

## Example 3: Note Taking App

### Customer Request
> "I want to take notes with markdown support"

### Key Decisions

- Editor: Contenteditable vs textarea
- Preview: Live side-by-side vs toggle
- Storage: Per-note files vs single collection

### Notable Outputs

**Tech Architecture:**
- Note collection with content field
- Markdown parsing with marked.js (CDN)

**Animations:**
- Tab switching transitions
- Save indicator fade

---

## Anti-Patterns to Avoid

### Don't Skip Agents
❌ Going directly from requirements to coding
✅ Complete all 8 phases for comprehensive spec

### Don't Over-Scope
❌ Adding features user didn't request
✅ Stick to clarified requirements

### Don't Assume Technology
❌ Assuming React/Vue needed
✅ Vanilla JS by default, recommend framework only if needed
