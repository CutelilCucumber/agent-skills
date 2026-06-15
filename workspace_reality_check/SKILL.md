---
name: workspace-reality-check
description: Prevent hallucinated paths, incorrect assumptions, and invalid filesystem operations.
version: 1.0.0
category: filesystem
tags: [workspace, verification, filesystem, anti-hallucination, path-validation, safety]
---

## When to Use

Always use before:

Reading files
Writing files
Executing filesystem commands
Referencing project structure
Using other filesystem-related skills

## Procedure

1. Establish current location:
  pwd
2. Verify target path:
ls -la <path>

or

test -e <path>
3. Determine whether the target is:
  Inside the workspace
  Outside the workspace
  Accessible by available tools
4. Confirm the target was discovered rather than assumed.
5. Re-check paths if files have been moved, renamed, created, or deleted.

## Verification Questions
Before acting, ask:

  Have I actually seen this path?
  Did I verify this file exists?
  Am I assuming a project structure?
  Is this path inside the workspace?

If any answer is uncertain, investigate first.

## Rules
The filesystem is reality.
Never trust assumed paths.
Never create files in unverified directories.
Never modify files that have not been located.
Re-verify after major filesystem changes.