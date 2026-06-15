---
name: file-manipulation
description: Safely create, edit, move, rename, and delete files.
version: 1.0.0
category: filesystem
tags: [files, editing, creation, modification, refactoring, write-operations]
---

## When to Use

Modifying source code
Creating files
Refactoring directories
Updating configuration
Generating project artifacts

## Procedure

0. Perform skill: workspace-reality-check
1. Verify target path:
  ls -la <path>
2. Read existing content before modification.
3. Make the smallest reasonable change.
4. Verify the result:
  git diff

  or

  cat <file>
5. Validate the project:
  npm test
  npm run build
  pytest

Use the project's appropriate validation commands.

6. Report:
  Files changed
  Paths affected
  Validation performed

## Workspace Rules
File tools are limited to the workspace.
Shell commands start in the workspace but can reach outside it.
Verify location before every write operation.
Keep project artifacts inside the workspace whenever possible.

## Rules
Never overwrite blindly.
Never write to unverified paths.
Verify edits after writing.
Validate changes when practical.