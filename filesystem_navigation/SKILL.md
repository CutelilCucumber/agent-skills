---
name: filesystem-navigation
description: Map the workspace and verify paths before referencing files or directories.
version: 1.0.0
category: filesystem
tags: [filesystem, paths, navigation, discovery, directories, workspace]
---

## When to Use

Looking for files
Looking for directories
Determining where code lives
Resolving relative paths
Verifying a target location before reading or writing

## Procedure
0. Perform skill: workspace-reality-check
1. Determine the current workspace:
  pwd
2. Map the directory structure:
  find . -maxdepth 2 -type d | sort

Increase depth only when necessary.

3. Locate relevant files:
  find . -name "package.json"
  find . -name "*.py"
  find . -name "*.js"
  find . -name "*.ts"
4. Verify every path before use:
  ls -la <path>

  or

  test -e <path>
5. If multiple matches exist, inspect each candidate before proceeding.

## Rules
Never invent paths.
Never assume standard project structures.
Verify paths before referencing them.
Prefer discovered paths over inferred paths.
Treat the filesystem as the source of truth.