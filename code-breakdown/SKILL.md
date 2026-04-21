---
name: code-breakdown
description: Deep, structured code explanation skill for any user level (beginner to expert). ONLY trigger this skill when the user explicitly types the command '/code-breakdown'. Do NOT trigger for any other phrasing, even if the user asks to explain code in other ways. This skill must never auto-trigger — it is strictly command-activated.
---

# Code Breakdown Skill

A structured, personalized skill for explaining any code — from a single function to a full system — in a way that matches the user's level and keeps them engaged throughout.

---

## Phase 0: Pre-Explanation Setup (Always Run First)

Before explaining anything, ask the user these questions in a single friendly message. Do NOT start explaining yet.

### Questions to ask:

1. **Level of understanding**
   > "How comfortable are you with this code or its concepts?"
   - 🟢 Beginner — I'm new to this / just learning
   - 🟡 Intermediate — I understand basics but want deeper clarity
   - 🔴 Expert — I just want a fast, dense walkthrough

2. **Familiarity with the language/framework**
   > "Have you worked with [detected language] before, or is this new to you?"
   (Detect the language from the code automatically and ask specifically about it)

3. **Block-by-block check-ins**
   > "After explaining each section, should I pause and ask if you have doubts — or just keep going?"
   - ✋ Pause after each block
   - ⏩ Keep going, I'll ask if I'm stuck

4. **Goal of understanding**
   > "What's your goal here?"
   - I want to fully understand every line
   - I just want to know what it does overall
   - I need to modify/debug it
   - I'm preparing for an interview

Store all answers internally. Use them to shape the entire explanation.

---

## Phase 1: Summary (Always First)

After collecting answers, start with a **plain-English summary** — 3 to 5 sentences max.

Cover:
- What is the overall purpose of this code?
- What problem does it solve?
- What does it take as input and produce as output (high level)?

**Format:** Prose only. No bullet points. No code yet.

---

## Phase 2: Top-Down Block-by-Block Explanation

Go through the code from top to bottom, section by section (logical blocks — imports, class/function definitions, loops, conditionals, return statements, etc.).

### For each block, explain:

- What this block is doing in plain terms
- What it takes in (parameters, variables from outer scope, etc.)
- What it produces or modifies (return value, side effect, state change)
- What built-in functions, methods, or libraries are used — and what they do

### Level-specific rules:

#### 🟢 Beginner
- Explain every line in detail, no skipping
- Show exact syntax of any function or method used:
  > e.g., "`split(separator)` — splits a string into a list. Syntax: `str.split(sep)`. Here it's splitting by comma."
- Explain **why this approach was chosen** (design intent) — e.g., "A dictionary is used here instead of a list because we need to look things up by name, not by position."
- Use simple, everyday language. Avoid jargon unless defined.
- After each block (if user chose pause mode): ask **"Any doubts here, or should we move on?"**

#### 🟡 Intermediate
- Skip defining very basic things (variable assignment, print statements, simple loops)
- No syntax breakdowns for common built-ins
- Do NOT explain design intent / "why written this way"
- Keep explanations tight and fast-paced but thorough
- After each block (if pause mode chosen): ask **"All good here?"**

#### 🔴 Expert
- Give a dense, compact explanation per block
- Focus only on logic, data flow, and non-obvious behavior
- Skip all basics entirely
- No pause check-ins unless user opted in
- Use technical terminology freely

---

## Phase 3: Bottom-Up Execution Flow

After the top-down walkthrough, switch perspective.

Tell the user:
> "Now let's flip it — I'll walk you through what actually happens when this code *runs*, step by step."

Trace the actual **execution order**:
- Which line/function gets called first?
- What data is passed into it?
- What does it return or trigger next?
- Continue until the final output

For **Beginner**: Walk through with a concrete sample input. Show what each variable holds at each step.
For **Intermediate**: Trace the flow at function/block level with key variable states.
For **Expert**: High-level execution path only, noting any non-obvious control flow.

### Artifact for this phase:
Generate **one of the following** based on what fits the code structure best:

- **Mermaid flowchart** — best for linear flows, conditionals, loops
- **React/HTML component** — best for complex multi-function flows, class interactions, async patterns, or anything that benefits from an interactive visual

Criteria for choosing:
- Simple scripts / single functions → Mermaid
- Multiple functions calling each other, classes, async/await, API flows → React/HTML component
- When in doubt → React/HTML (richer, more readable)

---

## Phase 4: Visual Summary Artifact

After both walkthroughs, generate a **visual summary artifact** that shows:
- Major components/blocks of the code
- Data flowing between them
- Execution sequence (numbered)

Again choose between Mermaid or React/HTML based on complexity (same criteria as Phase 3).

---

## Phase 5: Learning Check (Only After Full Explanation Is Done)

Once the entire explanation is complete, ask the user:

> "Want to test what you just learned? 🎯"

If yes, run **both** of the following:

### Mini Quiz (2–3 questions)
Ask questions that test understanding of the code just explained. Questions should be:
- Specific to the actual code (not generic)
- Progressively harder (easy → medium → tricky)
- Answered by the user before Claude reveals the answer

Example format:
> "Q1: What does the `results` variable hold after line 12 runs?"
> *(Take a guess before I reveal it!)*

Reveal the answer only after the user responds.

### "What If?" Challenge
Propose one small, targeted code change and ask the user to predict what happens:

> "What if I changed `[original]` to `[modified]`? What do you think would happen?"

Wait for the user's answer, then explain whether they were right and why.

---

## General Rules (Apply Always)

- Never start explaining before Phase 0 is complete
- Always detect the programming language automatically from the code
- Never paste large raw code blocks back to the user without explanation around them
- Keep tone friendly, patient, and encouraging — especially for beginners
- Never be condescending to any level
- If the user shares multiple files or a large codebase, ask: "Should I explain all of it, or is there a specific part you're confused about?"
- If code has a bug or an inefficiency, note it briefly but don't derail the explanation — stay focused on understanding first
