---
name: filesystem-tool-navigation-system
description: "Hierarchical filesystem interaction system with strict separation between path resolution, codebase inspection, and file operations."
version: 1.0.0
category: filesystem
tags: [filesystem, navigation, codebase, file-ops, workspace, verification, agent-tools]
status: stable
confidence: 0.42
source: learned
owner: brisonder
created: "2026-06-15T04:10:00Z"
---

# Filesystem Tool Navigation System

This system is divided into three non-overlapping layers:

1. Path Resolution (where am I / does this exist)
2. Codebase Introspection (how is this structured)
3. File Operations (make changes safely)

Each layer is independent and must not be mixed.

---

# 1. PATH RESOLUTION LAYER

## Purpose

Resolve whether a path exists and establish the current working location.

## When to Use

Use ONLY when:
- verifying a file or directory exists
- determining current location
- confirming a path before any other operation

Do NOT use for:
- reading file contents
- understanding code
- modifying files
- searching codebases

## Procedure

1. Check current directory:
```bash
pwd

2. Validate path existence:
```bash
test -e <path> && echo "exists"

3. Inspect target metadata:
```bash
ls -la <path>

## Output Rule

Return only:

existence confirmation
directory structure visibility

## No interpretation of code or system behavior.

Hard Constraints
No find
No rg
No file edits
No system reasoning beyond existence checks

# 2. CODEBASE INTROSPECTION LAYER

## Purpose

Understand structure, architecture, and relationships within a codebase.

## When to Use

Use ONLY when:

analyzing project structure
locating entry points
tracing logic flow
debugging behavior
understanding dependencies

Do NOT use for:

verifying file existence
modifying files
executing file operations

## Procedure

1. Identify project type:
```bash
find . -maxdepth 2

2. Locate entry points:
```bash
find . -name "main.*"
find . -name "app.*"
find . -name "index.*"

3. Search for logic:
```bash
rg "<symbol>"

4. Inspect file contents:
```bash
cat <file>

## Output Rule

Return:

structure overview
entry points
dependency flow

No file modification or path validation logic.

## Hard Constraints

No test -e
No ls -la <path> validation workflow
No writing or editing files
No operational execution

# 3. FILE OPERATION LAYER

## Purpose

Perform safe creation, modification, or deletion of files.

## When to Use

Use ONLY when:

a file path is already verified
a change has been explicitly defined
modification scope is clear

Do NOT use for:

discovery
codebase analysis
path validation
architecture reasoning

## Precondition (MANDATORY)

You must already know:

exact file path
file exists
intended operation

If not satisfied → STOP.

## Procedure

1. Inspect file:
```bash
cat <file>

2. Apply minimal modification.

3. Verify result:
```bash
git diff

or
```bash
cat <file>
4. Run project validation if applicable:
```bash
npm test
pytest
npm run build

## Output Rule

Return:

files modified
exact changes made
validation steps performed

## Hard Constraints

No find
No codebase exploration
No path discovery
No assumptions about filesystem state
No edits without verified path

# GLOBAL GUARDRAILS

These apply to all layers:

The filesystem is authoritative.
Paths must be observed, not inferred.
Each layer must be used independently.
Never mix validation, exploration, and modification steps.
Re-verify after any filesystem change.
