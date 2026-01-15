# Common Agent Tools

All agents in this plugin share a common set of tools and behaviors.

## Available Tools

### Read
- Read specifications, requirements, and reference materials
- Load `.shared/` folder outputs from previous agents
- Access reference guides in `references/` folder

### Write
- Create output files in `.shared/` folder
- Generate specification documents
- Produce deliverables in Markdown format

### Grep, Glob
- Search for code patterns in existing codebase
- Find relevant files and content
- Identify existing implementations to reference

### Agent-Specific Tools
| Agent | Additional Tools |
|-------|------------------|
| Interviewer | AskUserQuestion |
| Client Tech Architect | WebFetch |
| Browser QA | mcp__claude-in-chrome__* |

## .shared Folder Convention

All agents write outputs to the `.shared/` folder in the target repository:

```
[target-repo]/.shared/
├── 01-requirements.md      # Interviewer
├── 02-wireframes.md        # UI Sketcher
├── 03-ux-specification.md  # UX Spec Writer
├── 04-tech-architecture.md # Client Tech Architect
├── 05-flow-diagrams.md     # Mermaid Designer
├── 06-animations.md        # Interactive Designer
├── 07-roadmap.md           # Planner
└── 08-qa-report.md         # Browser QA
```

## Loading Previous Agent Outputs

When starting work, load relevant previous outputs:

```markdown
## Context Loading

1. Read `.shared/01-requirements.md` for requirements
2. Read `.shared/02-wireframes.md` for visual structure
3. Read `.shared/03-ux-specification.md` for UX details
```

## Output Format Guidelines

### Markdown Structure
- Use clear headings (##, ###)
- Include code blocks with language hints
- Add tables for structured data
- Keep sections focused and scannable

### Metadata Header
```markdown
---
agent: [agent-name]
created: [ISO timestamp]
input: [list of consumed files]
---
```

### Quality Standards
- Completeness: All required sections present
- Consistency: Follow established patterns
- Clarity: Easy to understand and use
- Actionable: Ready for next agent or implementation
