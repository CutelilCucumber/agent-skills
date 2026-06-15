---
name: codebase-exploration
description: Build an understanding of a codebase before making changes.
version: 1.0.0
category: filesystem
tags: [codebase, architecture, exploration, dependencies, search, debugging, context]
---

## When to Use

Working in an unfamiliar project
Tracing functionality
Locating routes, controllers, services, or components
Finding where a bug originates
Determining where code should be modified

## Procedure

1. Identify project type:
  find . -maxdepth 2 -name "package.json"
  find . -maxdepth 2 -name "requirements.txt"
  find . -maxdepth 2 -name "pyproject.toml"
2. Identify entry points:
  find . -name "main.py"
  find . -name "app.py"
  find . -name "index.*"
  find . -name "server.*"
3. Search for relevant symbols:
  rg "<symbol>"
4. Trace imports, dependencies, and call flow.
5. Read surrounding files before editing.
6. Form a mental model of:
  Entry points
  Data flow
  Dependencies
  Components involved

## Rules
Read before modifying.
Understand call flow before editing.
Verify assumptions through code inspection.
Search the codebase instead of guessing locations.