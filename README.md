# claudemd-doctor

`claudemd-doctor` is a CLI diagnostic and auto-remediation tool modeled after `brew doctor`. Its purpose is to audit, clean, and optimize the hierarchical stack of `CLAUDE.md` context files that agents (like Claude Code and Princess-Pi) read during operation.

*Note: This tool specifically targets the text semantics of `CLAUDE.md` files. It is distinct from Claude Code's native `/doctor` command, which diagnoses JSON config schema errors, API connectivity, and MCP server breakages.*

## Features
- **Hierarchical Discovery**: Walks the directory tree upwards starting from the Current Working Directory to identify the full context stack (Repo Level → Domain Level → User Level).
- **Semantic Analysis**: Identifies redundant statements, contradicting rules, and scope misalignment (e.g., global rules in repo context).
- **Diagnosis Report**: Scores context health and compares with community best practices.
- **Treatment Protocol**: Guides users through an interactive wizard to delete, merge, or move rules across the hierarchy, and suggests community snippets.

## Documentation
- [Initial Specification](docs/claudemd-doctor-spec.md)
