# Skill Detailed Guide

Comprehensive guide for webapp-consultant skill.

## When to Use

### Use When
- Customer request is vague or unclear
- Planning new web app from scratch
- Need comprehensive documentation before coding
- Building HTML + Tailwind + vanilla JS app
- Client-side only (no backend)

### Don't Use When
- Requirements already crystal clear
- Building backend/server-side application
- Need React/Vue/framework-specific planning
- Just need quick prototype

## Tech Stack Constraints

This skill targets **desktop web apps** with:

| Layer | Technology |
|-------|------------|
| Frontend | HTML + Tailwind CSS + vanilla JavaScript (ES6+) |
| Storage | LocalStorage (settings) + IndexedDB via localbase (data) |
| Backend | None (all client-side) |
| File System | Browser storage only |
| Target | Desktop-first, responsive for tablet/mobile |

## Agent Workflow Details

### Sequential Phase (Must Follow Order)

```
1. Interviewer
   ↓ (requirements.md)
2. UI Sketcher
   ↓ (wireframes.md)
3. UX Spec Writer
   ↓ (ux-specification.md)
```

### Parallel Phase (Can Run Simultaneously)

```
       ux-specification.md
              ↓
   ┌──────────┼──────────┐
   ↓          ↓          ↓
4. Tech    5. Mermaid  6. Interactive
   Architect   Designer    Designer
```

### Final Phase

```
7. Planner (needs all previous outputs)
   ↓
8. Browser QA (needs running app)
```

## Agent Delegation Pattern

When delegating to agents via Task tool:

```markdown
TASK: [Specific atomic goal]
EXPECTED OUTCOME: [Concrete deliverables]
REQUIRED AGENT: [Agent name]
CONTEXT: [File paths, patterns, constraints]

MUST DO:
- [Requirement 1]
- [Requirement 2]

MUST NOT DO:
- [Forbidden action 1]
- [Forbidden action 2]
```

## Reference Files by Task

| Task | Reference |
|------|-----------|
| Overall process | `workflow.md` |
| Customer interviews | `interview-patterns.md` |
| ASCII wireframes | `ascii-art-guide.md` |
| Data persistence | `localbase-guide.md` |
| UX documentation | `ux-philosophy.md` |
| Flowcharts | `mermaid-patterns.md` |
| Animations | `tailwind-animations.md` |
| Prioritization | `planning-methods.md` |
| Agent coordination | `shared-folder-spec.md` |
| Tech decisions | `spa-tech-stacks.md` |

## Success Criteria

A successful consultation produces:

- [ ] Clarified requirements with customer validation
- [ ] Visual wireframes showing all screens
- [ ] Technical specification with code examples
- [ ] Complete data architecture
- [ ] Flow diagrams for major features
- [ ] Animation specifications with Tailwind code
- [ ] Prioritized roadmap with realistic phases
- [ ] QA report confirming functionality
- [ ] Ready for immediate development start

## Tips for Effective Use

1. **Let interviewer finish**: Clear requirements save development time
2. **Review wireframes early**: Visual representation catches missing features
3. **Validate UX philosophy**: Ensure designs align with user needs
4. **Keep tech stack simple**: Optimize for vanilla JS
5. **Trust prioritization**: MoSCoW ensures realistic MVP scope
6. **Use full workflow**: Skipping agents leads to incomplete specs
7. **Check QA report**: Verify before considering done

## Post-Consultation Steps

After specification is complete:

1. Set up project structure (HTML, Tailwind config, JS modules)
2. Implement repository classes from tech architecture
3. Build UI components following wireframes
4. Connect UI to data layer
5. Add animations from interaction spec
6. Test against QA checklist
7. Deploy
