# Claude Code Learning Tutorial — Project Guide

## What We're Building

A single-file interactive HTML tutorial that teaches Claude Code fundamentals to Enterprise Architects. This is a **self-contained learning experience** — no backend, no build step, no dependencies beyond CDN-loaded libraries. Anyone on the team should be able to open the file in a browser and start learning immediately.

This tutorial will be demoed live in a presentation. It needs to look polished and professional — not like a generic tutorial template.

---

## Project Goals

- Teach 5 core Claude Code concepts progressively, in order
- Gate each section behind a reflection prompt or short quiz the learner must complete
- Track progress locally so learners can close the browser and pick up where they left off
- Feel like something worth using, not something worth closing

---

## The 5 Learning Sections (in order)

1. **What is Claude Code?**
   - What it is, what it isn't
   - How it differs from the Claude.ai chat interface
   - Why it matters for architects specifically

2. **Writing Effective Prompts**
   - Prompts as precise articulations of intent
   - The difference between vague and well-scoped prompts
   - Examples relevant to architecture work (system design, code review, doc generation)

3. **Understanding Context Windows**
   - What a context window is and why it matters
   - How to structure long conversations effectively
   - Common failure modes and how to avoid them

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

---

## Progress Gating Rules

Each section must be **completed before the next unlocks**. Completion means:
- The learner has read through the section content
- The learner has answered the reflection prompt or short quiz at the end of the section
- The answer has been submitted (a free-text field is fine — we're not grading, we're prompting reflection)

Do **not** require a "correct" answer. The goal is engagement and retention, not testing.

---

## Progress Persistence

Use `localStorage` to track:
- Which sections are complete (`completed: true/false` per section)
- The learner's name (ask on first load, store it, use it throughout)
- Reflection answers (store them so the learner can review their own notes)

On load, check localStorage and restore state. If a learner is returning, greet them by name and show them where they left off.

---

## Design Direction

This is for Enterprise Architects at Adobe — a design company. It cannot look generic.

- **Tone**: Refined and professional, with subtle warmth. Not corporate-cold, not startup-playful.
- **Color palette**: Dark background preferred (easier on eyes for extended reading). Use a strong accent color sparingly.
- **Typography**: Choose something distinctive. Avoid Inter, Roboto, Arial. Consider a serif for headings paired with a clean monospace or humanist sans for body.
- **Layout**: Clean sidebar navigation showing section progress + main content area. Progress indicators should feel satisfying to complete.
- **Animations**: Subtle. Section unlocks should feel rewarding — a small transition or reveal, not a fireworks show.
- **No external images** — use CSS, SVG, or unicode for any visual elements.

---

## Technical Constraints

- **Single HTML file** — everything inlined or loaded from CDN
- **No frameworks required** — vanilla JS is fine, but lightweight libraries from cdnjs.cloudflare.com are allowed if they add genuine value
- **No build step** — must open directly in a browser via `open index.html`
- **localStorage only** — no backend, no cookies, no external API calls
- **Accessible** — keyboard navigable, reasonable color contrast

---

## File Output

Save the file as `claude-code-tutorial.html` in the project root.

---

## How to Work With Me on This

When I ask you to build or modify this tutorial, here's how I want you to operate:

- **Think before you code.** If my request is ambiguous, ask one clarifying question before proceeding.
- **Build incrementally.** If I ask for the full tutorial at once, build section by section and confirm the structure looks right before filling in all content.
- **Don't over-engineer.** The simplest implementation that meets the spec is the right one. No unnecessary abstractions.
- **Call out tradeoffs.** If there's a meaningful design decision (e.g., how to handle localStorage errors gracefully), surface it briefly rather than silently choosing.
- **Keep content sharp.** The tutorial copy should be concise and intelligent — written for people who read fast and think architecturally. No padding, no hand-holding preamble.

---

## What Done Looks Like

A reviewer opening `claude-code-tutorial.html` should be able to:

1. Enter their name and start the tutorial immediately
2. Read Section 1, answer the reflection prompt, and see Section 2 unlock
3. Close the browser, reopen the file, and land back exactly where they left off
4. Complete all 5 sections and see a clear "you're done" state with their reflection notes summarized
5. Think: *"I'd actually use this."*
