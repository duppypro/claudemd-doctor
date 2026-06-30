# claudemd-doctor Specification

## Overview
`claudemd-doctor` is a CLI diagnostic and auto-remediation tool modeled after `brew doctor`. Its purpose is to audit, clean, and optimize the hierarchical stack of `CLAUDE.md` context files that agents (like Claude Code and Princess-Pi) read during operation.

*Note: This tool specifically targets the text semantics of `CLAUDE.md` files. It is distinct from Claude Code's native `/doctor` command, which diagnoses JSON config schema errors, API connectivity, and MCP server breakages.*

As developers accumulate rules, guidelines, and context, `CLAUDE.md` files often suffer from duplication, contradictory instructions, and scope creep. `claudemd-doctor` diagnoses these issues semantically and guides the user through fixing them.

## 1. Discovery Phase
The tool mimics the exact file-discovery behavior of standard AI agents:
- It starts at the Current Working Directory (CWD).
- It searches for a `CLAUDE.md` file.
- It walks up the directory tree to the user's home directory (`~`), collecting every `CLAUDE.md` file it finds along the way.
- It maintains the hierarchical order of these files (e.g., Repo-level → Domain-level → User-level).

## 2. Stage 1: Symptoms Detected
Once the stack of files is loaded, `claudemd-doctor` performs a semantic analysis using an LLM backend to identify "symptoms" of poor context management:

### A. Redundancy (Semantic Matching)
It does not just look for exact `grep` string matches. It analyzes the *intent* and *meaning* of statements. If the global `~/.pi/agent/CLAUDE.md` says "Always write tests in pytest" and a project-level `CLAUDE.md` says "Pytest must be used for all testing", this is flagged as redundant.

### B. Contradictions
It looks for rules that actively conflict. For example, if the domain-level `~/git-projects/CLAUDE.md` enforces `snake_case` for filenames, but the repository `CLAUDE.md` enforces `kebab-case`, the tool flags this contradiction for resolution.

### C. Scope Misalignment
It analyzes whether a rule belongs at its current level in the file hierarchy.
- **User Root (e.g., `~/.pi/agent/CLAUDE.md`):** Should only contain absolute global rules, persona identity, standard tool configs, or life-scheduling constraints (e.g., "Always use UTC", "Keep tone concise").
- **Domain Level (e.g., `~/git-projects/CLAUDE.md`):** Should only contain rules related to software engineering, coding conventions, architectural boundaries, or testing frameworks. It should *not* contain personal life scheduling rules (which belong in a hypothetical `~/personal-tasks/CLAUDE.md`).
- **Repo Level (e.g., `~/git-projects/my-app/CLAUDE.md`):** Should be strictly scoped to the exact tech stack, build commands, and specific architecture of that exact repository.

## 3. Stage 2: Diagnosis
After analyzing the symptoms, the tool outputs a **Diagnosis** report:

- **Overall Health Score:** 
  - 🟢 **Good Health:** Clean, minimal, well-scoped rules.
  - 🟡 **Needs Work:** Minor redundancies, some scope leakage.
  - 🔴 **Critical Admission to ER!:** Rampant contradictions, massive token bloat, or critical rules placed in the wrong scopes preventing agents from functioning properly.
- **Best Practices Comparison:** The tool compares the user's current context stack against known good practices from top AI-native coders (e.g., checking if the user adheres to the "Hierarchical Scoping Standard" or if they are wasting context window with excessive formatting rules).

## 4. Stage 3: Treatment Protocol
The tool presents an interactive CLI wizard proposing a treatment plan.

- **Actionable Decisions:** The wizard goes through the symptoms one by one, asking the user what to do:
  - **Delete:** Remove a redundant or outdated statement.
  - **Merge:** Combine two similar statements into a single, clearer rule.
  - **Move:** Migrate a statement up or down the hierarchy (e.g., moving a project-specific run command out of the global user config and down into the repo config).
- **Community Snippets:** `claude-doctor` suggests off-the-shelf, open-source `CLAUDE.md` snippets from the community (e.g., inserting standard Next.js 15 routing rules or standard Make vs Buy prompting templates).
- **Automated Editing:** Upon user confirmation, `claudemd-doctor` writes the exact changes back to the respective files.
- **Re-evaluation:** Once the treatment protocol is complete, `claudemd-doctor` automatically re-runs the discovery and diagnosis phases from the beginning to confirm a clean bill of health.
