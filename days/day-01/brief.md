# Day 1 - Python Environment and Core Refresh

Estimated focused time: 5-6 hours

Start with [lesson.md](lesson.md). Complete its checkpoints in order before
attempting the main build task.

## Main build task

Set up a Python 3.12 virtual environment and rebuild your practical Python foundation before starting FastAPI.

Create `projects/learning-tasks-api/scratch/day_01_task_summary.py`. It must:

- Store at least three learning tasks as dictionaries with `title`, `priority`, and `completed` fields.
- Use a function to print only incomplete tasks.
- Use a function to mark one task complete by title and return a useful result.
- Print a readable final summary that includes total and completed task counts.
- Include type hints on every function you create.

## Constraints

- Create every source file yourself. Do not copy a complete tutorial application.
- Do not use FastAPI today.
- Use only the Python standard library today; do not install packages.
- You may read the official Python tutorial sections for lists, dictionaries, control flow, and functions as references.
- Do not use classes today. Functions and dictionaries are enough.

## Suggested command sequence

Run these from the repository root in a new PowerShell terminal:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python --version
python -m pip --version
```

The `python` command is used because it resolves correctly to Python 3.12 on
this computer. Package installation is unnecessary today because the task uses
only Python's standard library.

If PowerShell blocks activation, report the exact error. Do not change execution policy without discussing it first.

## Small practice task

Create `projects/learning-tasks-api/notes/day-01-python-foundations.md`. In your own words, explain:

1. Why a virtual environment exists.
2. The difference between a list and a dictionary, using your task data as an example.
3. Why a function with a type hint is easier to maintain than repeated code.
4. What a `for` loop and an `if` condition do in your script.
5. One mistake you made today and how you corrected it.

## Done criteria

- The virtual environment is active and `python --version` shows Python 3.12.
- The script runs without an exception.
- The script uses lists, dictionaries, a loop, conditions, functions, and type hints.
- Notes are written in your own words.
- One Git commit is created with a message such as `feat: add task summary script`.

## Evening review submission

Complete `days/day-01/review.md`, commit your work, push to GitHub, then send me the commit link.
