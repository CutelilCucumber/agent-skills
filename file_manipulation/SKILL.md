Skill: file_manipulation
Use Case

Use this skill whenever creating, editing, moving, renaming, or deleting files.

This skill governs all agent actions that change the filesystem.

How
Principle

Verify first. Modify second.

The file tool is workspace-scoped.

Shell commands may reach outside the workspace.

Treat this distinction carefully.

Step 0: use the Skill: workspace_reality_check

Step 1: Verify Target

Confirm location:

pwd

Verify target:

ls -la target/path

or

test -e target/path
Step 2: Confirm Workspace Boundaries

Before any write operation determine:

Is the target inside the workspace?
Is the target outside the workspace?
Is the file tool capable of reaching it?

If uncertain:

Stop and investigate.

Step 3: Inspect Existing Content

Before modifying:

cat target/file

or read using file tools.

Understand the current state before changes.

Step 4: Apply Minimal Changes

Prefer:

Small edits
Focused patches
Preservation of existing structure

Avoid unnecessary rewrites.

Step 5: Validate Results

After modification:

cat target/file

or

git diff

Verify the intended change exists.

Step 6: Validate Project Integrity

When applicable:

npm run build
npm test
pytest
cargo test

or the project's standard validation command.

Step 7: Report Outcomes

Document:

Files changed
Paths affected
Validation performed
Remaining concerns
Special Workspace Rules
File tools operate only within the workspace.
Shell commands begin in the workspace but are not sandboxed.
Never assume a shell-created file can later be accessed by the file tool.
Prefer keeping all project artifacts inside the workspace.
Verify location before every write operation.
Rules
Never overwrite without inspection.
Never create files in guessed locations.
Verify path existence before modification.
Validate changes after writing.
Prefer workspace-local operations.
Success Criteria
Correct target identified.
File modified intentionally.
Changes verified.
Project remains functional.
Tags

file-editing
filesystem
agent-actions
workspace
write-operations
modification
validation
creation
refactoring