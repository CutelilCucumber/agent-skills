Skill: workspace_reality_check
Use Case

Use this skill whenever:

A path is mentioned in the conversation.
A file is going to be read, edited, moved, renamed, or deleted.
A shell command references a filesystem location.
A new file is being created.
The user refers to a directory that has not been verified.
A previous tool call failed because a file or directory could not be found.
The task spans multiple tool calls and filesystem state may have changed.

This skill should be executed before any filesystem operation when uncertainty exists.

How
Principle

The filesystem is reality.

User descriptions, prior observations, memory, and assumptions are not reality.

Only the current filesystem state is authoritative.

Step 1: Establish Current Reality

Run:

pwd

Record the current working directory.

Treat this as the starting point for all path reasoning.

Step 2: Verify Workspace Scope

Determine:

What directory the tools are scoped to.
Whether the target path is inside or outside the workspace.
Whether the requested operation can be completed with available tools.

Remember:

File tools are confined to the workspace.
Shell commands begin in the workspace but may access locations outside it.
A workspace is a tool boundary, not a security boundary.
Step 3: Verify Every Referenced Path

For every path mentioned by the user or the agent:

ls -la <path>

or

test -e <path> && echo exists

Do not continue until the path is confirmed.

Step 4: Resolve Relative Paths

Never assume the meaning of:

./
../
src/
app/
backend/
server/

Verify their actual location from the current working directory.

Use:

realpath <path>

when available.

Step 5: Confirm Target Before Action

Before any modification:

Verify:

The file exists.
The directory exists.
The path points to the intended target.
No duplicate files create ambiguity.

If multiple candidates exist:

Stop and investigate.

Step 6: Revalidate After State Changes

Repeat verification whenever:

Files are created.
Files are moved.
Files are renamed.
Directories are created.
Git branches change.
Build tools generate new artifacts.

Do not rely on earlier observations.

Step 7: Detect Assumptions

Before executing a filesystem action, ask:

Was this path discovered or assumed?
Was this file verified or inferred?
Was this location observed in the current session?

If the answer is "assumed," perform verification.

Failure Conditions

Immediately stop and investigate if:

A path cannot be verified.
Multiple matching files exist.
The target location differs from expectation.
Workspace boundaries are unclear.
The requested operation depends on an unverified assumption.
Rules
Never invent paths.
Never trust remembered paths.
Never assume standard project structures.
Never create files in unverified directories.
Never edit files that have not been located.
Treat every filesystem operation as requiring proof.
Pre-Action Checklist

Before any file operation confirm:

Current directory verified.
Workspace understood.
Target path exists or intended parent directory exists.
Path was observed, not assumed.
Tool access to the target is confirmed.
Success Criteria
Filesystem state verified.
Workspace boundaries understood.
Target path confirmed.
No filesystem assumptions remain.
All actions are based on observed reality.
Tags

workspace
reality-check
path-validation
filesystem
verification
safety
file-operations
agent-foundation
navigation
anti-hallucination