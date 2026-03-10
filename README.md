# Claude Code Tutorial

An interactive, self-contained HTML tutorial that teaches Claude Code to Enterprise Architects — built entirely using Claude Code itself.

This project is both the artifact and the demonstration: the tutorial was conceived, designed, and written through a conversation with Claude Code, using nothing but a `CLAUDE.md` file as the starting specification. It's a practical example of what agentic, iterative development with Claude Code looks like in practice.

---

## What It Is

`claude-code-tutorial.html` is a single-file, browser-based learning experience covering 11 progressive sections:

1. What is Claude Code?
2. Writing Effective Prompts
3. Understanding Context Windows
4. Agentic Workflows
5. MCP Basics
6. Plan Mode & Execution Modes
7. Tools — Built-in Capabilities
8. Subagents
9. Choosing the Right Model
10. Plugins, Hooks & IDE Integration
11. What's Next — resources and next steps

Each section includes prose content, prompt examples, and a 3-question multiple choice knowledge check. Sections unlock sequentially. Progress, quiz scores, and the learner's name persist in `localStorage` — close the browser and resume exactly where you left off.

---

## Running It

No installation, no build step, no server required.

```bash
git clone https://github.com/jeffhlewis/Claude-Code-Tutorial.git
cd Claude-Code-Tutorial
open claude-code-tutorial.html   # macOS
# or: start claude-code-tutorial.html  (Windows)
# or: xdg-open claude-code-tutorial.html  (Linux)
```

That's it. The file is fully self-contained — fonts load from Google Fonts CDN, everything else is inlined.

---

## How This Was Built

This project started with a single `CLAUDE.md` file describing the desired output. Claude Code — running in a terminal, with access to the filesystem — did the rest through an iterative conversation.

### The process

**1. Write a spec, not a prompt**

The `CLAUDE.md` file defined the project goals, section structure, design direction, and acceptance criteria before a single line of code was written. Claude Code reads this file at the start of every session, so it provides persistent context across all interactions.

**2. Build incrementally, validate often**

Rather than requesting the full tutorial at once, the build followed the sequence in CLAUDE.md — HTML skeleton, then CSS, then JavaScript state management, then section content, then features like quiz logic and animations. Each step was verified before the next began.

**3. Iterate conversationally**

Features were added, changed, and removed through natural language:
- *"Add a multiple choice quiz to each section"*
- *"Remove the reflections feature"*
- *"Add additional sections on plan mode, subagents, tools, and model selection"*
- *"Add a final section with links to next-level resources"*

Claude Code translated each instruction into targeted edits — reading the existing file, understanding what was already there, and making precise changes without breaking what worked.

**4. Claude Code managed git too**

Branching, staging, committing, and pushing were all done through Claude Code. The PR description was drafted by Claude Code based on the actual diff.

### What this demonstrates

- A well-written `CLAUDE.md` is the highest-leverage investment in any Claude Code project
- Complex, stateful single-file applications are well within Claude Code's scope when built incrementally
- Conversational iteration — adding, removing, and reshaping features — works cleanly when the codebase is well-structured
- Claude Code can manage the full development workflow, not just the code

---

## Recreating This Yourself

You can build your own version of this tutorial — or something entirely different — by following the same approach.

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/quickstart) installed and authenticated
- A GitHub repo (or any local directory)

### Step 1: Write your CLAUDE.md

This is the most important step. Your `CLAUDE.md` should define:

- **What you're building** — one clear paragraph describing the artifact and its purpose
- **Project goals** — 3–5 bullet points on what success looks like
- **Structure** — the sections, features, or components you want
- **Design direction** — tone, visual style, constraints
- **Technical constraints** — single file? No framework? Specific CDNs?
- **How to work with you** — how Claude Code should behave (ask before assuming, build incrementally, etc.)
- **What done looks like** — concrete acceptance criteria a reviewer could verify

The more specific and opinionated your CLAUDE.md, the less ambiguity Claude Code has to resolve on its own — and the closer the first output will be to what you want.

### Step 2: Start with the skeleton

Ask Claude Code to build the structure first, before filling in content:

```
Build the HTML skeleton and CSS layout described in CLAUDE.md.
Include the welcome screen, app shell with sidebar, and main content area.
Don't add section content yet — just the structural scaffolding.
```

Verify it looks right in a browser before continuing.

### Step 3: Add one feature at a time

Work through the build sequence in logical layers — layout, then state management, then content, then interactions, then polish. Each conversation turn should have a clear, bounded scope.

```
Add the localStorage state management. The state object should track
learner name, current section, and completion status per section.
Wire up the welcome screen to initialize state and transition to the app.
```

### Step 4: Iterate freely

Once you have a working base, Claude Code handles change well. Be direct:

```
Remove the X feature
Add Y to each section
Change the gating mechanic from Z to Q
```

Claude Code will read what's already there and make targeted edits. You don't need to re-explain the whole codebase — it reads the file.

### Step 5: Use Plan Mode for complex changes

For changes that touch many parts of the file at once — adding a new feature that requires updates to CSS, JS state, and multiple render functions — activate plan mode first:

```
/plan
Add a progress percentage display to the sidebar footer that updates
as sections are completed.
```

Review the plan before approving execution. It's the difference between a precise set of edits and a surprise refactor.

### Tips

- **Keep sections focused.** One concern per conversation turn. "Add the quiz feature" is better than "add the quiz feature and also fix the mobile layout and update the color scheme."
- **Verify in the browser often.** Claude Code can't see the rendered output — you're the quality gate.
- **Commit working states.** Before any large change, commit what you have. Claude Code can handle git: `git add`, `git commit`, `git push`, and `gh pr create` all work through the Bash tool.
- **Update CLAUDE.md as the project evolves.** When you remove a feature or change an architectural decision, update the spec. Future sessions will be grounded in the current reality, not the original plan.

---

## Project Structure

```
Claude-Code-Tutorial/
├── claude-code-tutorial.html   # The complete tutorial — open this in a browser
├── CLAUDE.md                   # Project specification for Claude Code
└── README.md                   # This file
```

---

## Tech Stack

| Concern | Approach |
|---|---|
| Structure | Vanilla HTML, single file |
| Styling | Inline CSS with custom properties |
| Logic | Vanilla JavaScript |
| Fonts | Google Fonts CDN (Lora, DM Sans, JetBrains Mono) |
| Markdown | Marked.js via cdnjs |
| Persistence | `localStorage` |
| Build step | None |

---

## License

MIT
