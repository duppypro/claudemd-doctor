# Project Bootstrapping Rules (NEW_REPO_CLAUDE.md)

Welcome, Agent. You have just been initialized in a newly spun-off workspace. Before you write any code or make file changes, you must establish the project environment.

This project inherits:
1. **Global Persona & Identity:** defined in `~/.pi/agent/CLAUDE.md`.
2. **Domain Process Standards:** defined in `~/git-projects/CLAUDE.md` (including Make vs Buy, 5-Step Commit Flow, and git etiquette).

---

## 🛑 MANDATORY STEP 1: Interview the Human Partner (Duppy)

You must immediately halt and grill the specification by asking Duppy the following scoping questions. Do not attempt to write code or create deep directories until these are clarified.

### 1. Project Type
*   What type of project is this?
    *   *Examples: Simple file/docs store, Pi/Claude extensions, CLI/Web apps, embedded firmware, GitHub wiki, etc.*

### 2. Tech Stack & Environment
*   What runtime, language, compiler, package manager, or frameworks are we using?
    *   *Examples: Node.js (ESM, TypeScript, esbuild), Python (pytest), Rust (cargo), C/C++ (CircuitPython/Wokwi), etc.*

### 3. Directory Map
*   What is the folder layout for this repository?
    *   *Note: Under domain rules (`~/git-projects/CLAUDE.md`), you must use `/tests` for permanent repeatable test suites, `/debug` for short-lived ephemeral diagnostics, and `/research` for prototypes/links.*
    *   Where does production source code live (e.g., `src/`, `bin/`, `lib/`)?

### 4. Local CLI Commands
What are the exact, zero-token bash commands to execute in this directory for:
*   **Spec Creation / Validation:**
*   **Build / Compile / Bundle:**
*   **Running Tests:**
*   **Linting / Formatting:**
*   **Deploy / Live Run:**

---

## 📋 UNIVERSAL CORE RULE: Issue-Driven Memory & Tracking

Regardless of whether this is a massive application or a simple documentation wiki:
*   **GitHub Issues are the Authoritative Memory:** You **must** open a GitHub issue for every feature, bug, or tangent before working on it.
*   **Master Status Tracking:** You **must** maintain a designated, always-open "Project status & human action items" issue. Update it as often as you commit so that progress and next steps are transparent and never lost.
*   **Attribution & Signature:** Always sign your issue comments and commits with your Princess-Pi credentials: `— 👑π🐱 Princess-Pi`.

---

## 🚀 STEP 2: Rewrite this CLAUDE.md

Once Duppy has provided the answers to the interview above:
1. Overwrite this file (`CLAUDE.md`) to permanently hardcode the decided Tech Stack, Directory Map, and local CLI Commands.
2. Preserve the references to global/domain standards and the Universal Core Rule for Issue-Driven Memory.
3. Commit the updated file under `Spec Approved` or `Research: Bootstrapped <project-name>` to lock in the project's execution environment.