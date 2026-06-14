# Fog2PRD

**From Foggy Requirements to PRD — One AI Skill Pipeline.**

Fog2PRD is an AI skill that transforms raw, ambiguous product requirements into structured, ship-ready deliverables. It follows a prototype-first workflow: clarify → visualize → document → handover.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## What It Does

| Stage | What Happens | Output |
|-------|-------------|--------|
| **1. Understand** | Analyzes input, detects ambiguities, asks clarifying questions | Requirements understanding report |
| **2. Prototype** | Generates interactive HTML prototypes, iterates with user feedback | Clickable HTML prototype + flow diagrams |
| **3. Document** | Produces formal PRD from confirmed prototype | Signed-off PRD document |
| **4. Handover** | Creates lightweight dev handover spec with wireframes | Developer handover note + wireframes |

### Core Design Principles

- **Prototype-first** — users confirm what they see, not what they read
- **Iterative refinement** — prototype rounds until alignment
- **Dual output** — formal sign-off docs + lightweight dev handover
- **5-minute dev handover** — devs get the gist fast

---

## Supported Input Types

- Verbal requirements (user dictation)
- High-level requirement documents
- Meeting notes and feature requests
- Any ambiguous product ask

---

## Deliverables

| Deliverable | Format | Audience |
|------------|--------|----------|
| Requirements Understanding Report | Markdown | Product Manager |
| Interactive HTML Prototype | HTML + CSS + JS | Stakeholders |
| Business Flow Diagram | Excalidraw | All |
| Formal PRD Specification | Markdown (formal template) | Sign-off / Archive |
| Dev Handover Note | Markdown (lightweight) | Engineering |
| Page Wireframes | Excalidraw (quick mode) | Engineering |

---

## How It Works

```
Raw Input → [Stage 1: Clarify] → [Stage 2: Prototype & Iterate] → [Stage 3: Formal PRD] → [Stage 4: Dev Handover]
```

### Stage 1: Requirements Understanding

Parses the input, extracts roles and features, scores complexity, and asks targeted clarification questions.

**Complexity scoring:**

| Dimension | Simple (1pt) | Medium (2-4pts) | Complex (5pts) |
|-----------|-------------|-----------------|----------------|
| Feature count | ≤3 | 4-8 | >8 |
| User roles | 1 | 2-3 | >3 |
| Business rules | Straightforward | Conditional branches | Multi-layer nesting |
| System integration | None | Single system | Multi-system |
| Data processing | Basic CRUD | Calculations | Complex algorithms |

**Score → Action:**
- 1-3: Quick confirm → prototype
- 4-7: Q&A clarification → prototype
- 8-10: Step-by-step confirmation → prototype

### Stage 2: Prototype Design & Iteration

Generates interactive HTML prototypes using modern UI patterns (cards, shadows, transitions, Lucide icons). Supports unlimited iterations until user sign-off.

### Stage 3: Formal PRD Generation

Compiles the confirmed prototype into a formal PRD document with full specs, business rules, data rules, and approval records.

### Stage 4: Developer Handover

Creates a lightweight handover document with:
- Core requirements summary
- Prototype links
- Business flow diagrams
- Quick page wireframes (low-fi fast mode)

---

## Example Flow

```
User: "I need a task management tool for my team..."

Fog2PRD: 📋 Let me clarify a few things first.
         Q1: How many team members?
         Q2: What's the most painful part of your current workflow?
         ...

User: [Answers]

Fog2PRD: 🖥️ Prototype ready. Please try it: [prototype link]
         Does this match your vision?

User: "Almost — can we change the sidebar layout?"

Fog2PRD: 🔄 Iterated. Try again: [updated link]

User: ✅ Confirmed.

Fog2PRD: 📄 PRD document generated: [doc link]
         📋 Dev handover generated: [handover link]
```

---

## Dependencies

This skill is designed for Hermes Agent and relies on these companion skills:

| Skill | Purpose |
|-------|---------|
| [frontend-design](https://github.com/dawni/frontend-design) | High-quality HTML prototype generation |
| excalidraw-diagram | Business flow and wireframe diagrams |
| obsidian-markdown | Markdown document processing |

---

## Installation

```bash
# Install via Hermes Agent
hermes install fog2prd

# Or clone manually
git clone https://github.com/dawni/fog2prd.git ~/.hermes/skills/fog2prd
```

Then trigger it naturally in conversation:

> *"We need a new user onboarding flow..."*
> *"Generate PRD for the dashboard redesign"*
> *"Design requirements for the mobile app"*

---

## Roadmap

- [ ] Template customization UI
- [ ] Export to PDF/Word
- [ ] Multi-language PRD generation
- [ ] Integration with Jira/Linear for automatic ticket creation

---

## License

MIT

---

## Author

[Dawni](https://github.com/dawni) — Product engineer building better tools for builders.
