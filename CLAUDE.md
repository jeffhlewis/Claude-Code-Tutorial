# Claude Code Learning Tutorial — Project Guide

## What We're Building

A single-file interactive HTML tutorial that teaches Claude Code to Enterprise Architects. This is a **self-contained learning experience** — no backend, no build step, no dependencies beyond CDN-loaded libraries. Anyone on the team should be able to open the file in a browser and start learning immediately.

This tutorial will be demoed live in a presentation. It needs to look polished and professional — not like a generic tutorial template.

---

## Project Goals

- Teach 11 Claude Code concepts progressively, in order
- Gate each section behind a 3-question multiple choice quiz the learner must complete
- Track progress locally so learners can close the browser and pick up where they left off
- Feel like something worth using, not something worth closing

---

## The 11 Learning Sections (in order)

1. **What is Claude Code?**
   - What it is, what it isn't
   - How it differs from the Claude.ai chat interface
   - Why it matters for architects specifically

2. **Writing Effective Prompts**
   - Prompts as precise articulations of intent
   - The Scope / Format / Constraints framework
   - Examples relevant to architecture work (system design, code review, doc generation)

3. **Understanding Context Windows**
   - What a context window is and why it matters
   - How to structure long conversations effectively
   - CLAUDE.md vs. chat — what belongs where
   - Common failure modes (context drift, file flooding) and how to avoid them

4. **Agentic Workflows**
   - What "agentic" means in practice
   - How Claude Code can execute multi-step tasks autonomously
   - When to use agentic mode vs. conversational mode
   - Human-in-the-loop patterns

5. **MCP Basics (Model Context Protocol)**
   - What MCP is and why it exists
   - Analogy: MCP is to AI agents what REST APIs are to microservices
   - Common MCP use cases for enterprise architects
   - How to think about MCP when evaluating AI system designs

6. **Plan Mode & Execution Modes**
   - What plan mode is and how to activate it (`/plan`, `Shift+Tab`)
   - When plan mode earns its cost vs. when to skip it
   - Default mode permission prompts and the human-in-the-loop mechanism
   - Plan as a commit on intent

7. **Tools — Built-in Capabilities**
   - Full tool taxonomy: Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch, Agent
   - Edit-over-Write principle
   - The tool use loop — inspect, approve, deny, redirect
   - Permission configuration (auto-allowed vs. requires approval)

8. **Subagents**
   - What the Agent tool does and how subagents work
   - Context isolation and worktree isolation
   - Parallel dispatch patterns
   - Specialized agent types: Explore, Plan, general-purpose, feature-dev variants

9. **Choosing the Right Model**
   - Claude Opus 4, Sonnet 4.6, Haiku 4.5 — tradeoffs and use cases
   - The three decision axes: capability, cost, latency
   - Practical heuristics for right-sizing model selection

10. **Plugins, Hooks & IDE Integration**
    - VS Code and JetBrains IDE integrations
    - The Hooks system as a governance layer (PreToolUse, PostToolUse)
    - Custom slash commands in `.claude/commands/`
    - What a mature enterprise Claude Code deployment looks like

11. **What's Next**
    - Synthesis and closing
    - Curated resource cards linking to official documentation and next-level references
    - Anthropic docs, MCP spec, API reference, model overview, research

---

## Progress Gating Rules

Each section must be **completed before the next unlocks**. Completion means:
- The learner has read through the section content
- The learner has answered all 3 multiple choice questions in the knowledge check quiz
- The learner has clicked "Check answers" to see results
- The learner has clicked "Continue →" to advance

Quizzes show which answers are correct and which are wrong. Wrong answers display an explanation. A correct answer is required for the "Continue" button to unlock — but the quiz is educational, not punitive. The goal is reinforcement and retention.

---

## Progress Persistence

Use `localStorage` (key: `cc_tutorial_state`) to track:
- `learnerName` — asked on first load, used throughout for personalization
- `currentSection` — which section the learner is viewing
- Per-section: `completed`, `quizAnswers`, `quizSubmitted`, `quizScore`

On load, check localStorage and restore state. Returning learners skip the welcome screen and land directly on their active section.

localStorage errors degrade silently; a one-time banner is shown if storage is unavailable (e.g., private browsing).

---

## Design Direction

This is for Enterprise Architects at Adobe — a design company. It cannot look generic.

- **Tone**: Refined and professional, with subtle warmth. Not corporate-cold, not startup-playful.
- **Color palette**: Dark background preferred (easier on eyes for extended reading). Warm amber accent (`#E8A87C`) used sparingly.
- **Typography**: Lora (serif, headings) + DM Sans (humanist sans, body) + JetBrains Mono (code/prompts). Not Inter, Roboto, or Arial.
- **Layout**: Fixed 260px sidebar with section nav and progress bar + main content area. Progress indicators should feel satisfying to complete.
- **Animations**: Subtle. Section unlocks trigger a warm amber `unlockPulse` glow on the nav item. Content transitions use a `fadeIn` (opacity + translateY). No fireworks.
- **No external images** — CSS, SVG, and unicode only for visual elements.

---

## Technical Constraints

- **Single HTML file** — everything inlined or loaded from CDN
- **No frameworks** — vanilla JS; Google Fonts and Marked.js (cdnjs) are the only external dependencies
- **No build step** — must open directly in a browser via `open claude-code-tutorial.html`
- **localStorage only** — no backend, no cookies, no external API calls
- **Accessible** — keyboard navigable, `aria-label`/`aria-live`/`aria-current` throughout, WCAG AA contrast, `:focus-visible` styles
- **Responsive** — sidebar collapses at 768px

---

## File Output

`claude-code-tutorial.html` in the project root.

---

## How to Work With Me on This

When asked to build or modify this tutorial:

- **Think before coding.** If a request is ambiguous, ask one clarifying question before proceeding.
- **Don't over-engineer.** The simplest implementation that meets the spec is the right one. No unnecessary abstractions.
- **Call out tradeoffs.** Surface meaningful design decisions briefly rather than silently choosing.
- **Keep content sharp.** Tutorial copy should be concise and intelligent — written for people who read fast and think architecturally. No padding, no hand-holding preamble.
- **Adding sections**: new sections need an entry in `SECTIONS`, a corresponding entry in `QUIZ_DATA` (3 questions with correct index + explanation), and a `renderSectionN(container)` function. The rest of the system auto-adapts.

---

## What Done Looks Like

A reviewer opening `claude-code-tutorial.html` should be able to:

1. Enter their name and start the tutorial immediately
2. Read Section 1, answer the 3-question quiz, click "Continue →", and see Section 2 unlock with a glow animation
3. Close the browser, reopen the file, and land back exactly where they left off
4. Navigate back to a completed section and see their original quiz answers with correct/incorrect highlighting preserved
5. Complete all 11 sections and see a completion screen showing their total score across all 33 questions
6. Click "Reset progress" → confirm → return to the welcome screen with blank state
7. Think: *"I'd actually use this."*
