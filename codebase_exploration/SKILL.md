Skill: codebase_exploration
Use Case

Use this skill whenever a task requires:

Understanding an unfamiliar project
Finding where functionality lives
Tracing APIs, routes, services, or components
Locating configuration files
Building context before making changes

Use this skill before editing code.

How
Principle

Understand before modifying.

Build a mental model of the codebase before taking action.

Step 0: use the Skill: workspace_reality_check

Step 1: Identify Project Type

Look for:

find . -maxdepth 2 -name "package.json"
find . -maxdepth 2 -name "requirements.txt"
find . -maxdepth 2 -name "pyproject.toml"
find . -maxdepth 2 -name "Cargo.toml"
find . -maxdepth 2 -name "go.mod"

Determine:

Language
Framework
Build system
Step 2: Locate Entry Points

Examples:

Node:

cat package.json

Python:

find . -name "main.py"
find . -name "app.py"

Framework-specific:

find . -name "server.*"
find . -name "index.*"
Step 3: Build a Context Map

Identify:

Routes
Controllers
Services
Database layer
Configuration
Shared utilities

Search:

grep -R "target_function" .

or

rg "target_function"
Step 4: Trace Dependencies

Determine:

What imports the target file
What the target imports
What side effects may occur
Step 5: Read Before Editing

Inspect:

Target file
Neighboring files
Configuration files
Relevant tests

Do not edit based on filename assumptions alone.

Step 6: Create a Working Theory

Before changes, identify:

What component owns the behavior
What files will likely be affected
How changes propagate through the system
Rules
Read before modifying.
Understand call flow before editing.
Verify assumptions through code inspection.
Prefer search results over intuition.
Never treat a file name as proof of responsibility.
Success Criteria
Project type identified.
Entry points located.
Relevant components mapped.
Dependencies understood.
Modification targets confirmed.
Tags

codebase
exploration
analysis
context
architecture
investigation
routes
dependencies
search