Skill: filesystem_navigation

Usage

Use this skill whenever a task involves:

Finding files or directories
Understanding project structure
Determining where a file should be created
Resolving relative or absolute paths
Verifying that a path exists before using it

Use this skill before any file modification if the target location is uncertain.

How
Principle

Never assume a path exists.

Always discover and verify the filesystem before referencing locations.

The workspace is the default source of truth.

Step 0: use the Skill: workspace_reality_check

Step 1: Identify Workspace Root

Run:

pwd

Record the workspace root.

Treat this location as the authoritative project root unless evidence suggests otherwise.

Step 2: Map the Directory Structure

For small projects:

find . -maxdepth 3 -type d | sort

For large projects:

find . -maxdepth 2 -type d | sort
Step 3: Locate Relevant Files

Use targeted searches:

find . -name "package.json"
find . -name "tsconfig.json"
find . -name "*.prisma"
find . -name "*.py"

When searching by filename:

find . -iname "*keyword*"
Step 4: Verify Paths

Before reading or writing:

ls -la path/to/target

or

test -e path/to/target && echo exists
Step 5: Resolve Ambiguity

If multiple matching files exist:

Stop.
Present options.
Ask for clarification or infer from surrounding project structure.

Never guess.

Rules
Never invent folders.
Never assume src/, app/, backend/, or server/ exist.
Verify every target path before use.
Prefer discovered paths over user-described paths.
Re-check paths if significant filesystem changes occur.
Success Criteria
Workspace root identified.
Relevant directory structure mapped.
Target path verified.
No filesystem assumptions remain.

Tags

filesystem
paths
navigation
workspace
directory-mapping
path-validation
discovery