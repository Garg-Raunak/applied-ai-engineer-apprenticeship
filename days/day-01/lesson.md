# Day 01 Lesson - Python From the Beginning

## Outcome

By the end of today, you should be able to:

- explain what Python, an interpreter, a source file, a terminal, an IDE, and a
  virtual environment are;
- open the apprenticeship repository in VS Code;
- create and activate a virtual environment;
- create and run a Python file from the terminal;
- use variables, core data types, operators, strings, lists, dictionaries,
  conditions, loops, functions, and type hints;
- read the final line of a traceback and locate the failing source line;
- build the Day 01 task-summary script yourself;
- inspect the Git diff and commit the finished work.

Complete the checkpoints in order. Type the code yourself. Do not paste a full
solution from an article or ask an AI tool to generate the finished task.

## 1. Tools and vocabulary

### Python

Python is both a programming language and, in everyday conversation, the name
used for the program that executes Python code.

A file such as `hello.py` contains source code. The `.py` extension tells tools
that it is a Python source file.

### Interpreter

The Python interpreter is the executable program `python.exe`. It reads Python
source code, checks its syntax, and executes its instructions.

When you run:

```powershell
python hello.py
```

PowerShell starts `python.exe` and gives `hello.py` to it as an argument.

### Terminal and PowerShell

A terminal is a text interface used to run programs. PowerShell is the command
shell inside the terminal on this Windows computer.

The prompt displays the current directory. A command normally operates on that
directory unless you supply another path.

Useful PowerShell commands:

```powershell
Get-Location
Get-ChildItem
Set-Location "C:\path\to\directory"
```

- `Get-Location` prints the current directory.
- `Get-ChildItem` lists its contents. The aliases `dir` and `ls` also work, but
  we will learn the full command names first.
- `Set-Location` changes directory. The alias `cd` is commonly used.
- Quotation marks keep a path containing spaces together as one argument.

### IDE and editor

An editor changes text files. An IDE combines editing with code completion,
error checking, navigation, terminal integration, debugging, and other
development tools.

We will use **Visual Studio Code** because this career path combines Python,
FastAPI, JavaScript or TypeScript, React, SQL, Docker, Git, and cloud tooling.
VS Code supports all of them in one workspace and is widely used in software
teams. PyCharm is an excellent Python-specific alternative, but changing tools
will not improve your Python skill. Jupyter notebooks are useful later for data
experiments; they are not our main environment for backend services.

Installed VS Code support:

- **Python extension:** runs, tests, debugs, and discovers Python environments.
- **Pylance:** provides code completion, navigation, and type checking.

## 2. Open the correct repository

Open a new PowerShell terminal and run:

```powershell
cd "C:\Users\Raunak\Documents\ChatGPT\Career Revamp\applied-ai-apprenticeship"
Get-Location
Get-ChildItem
code .
```

`code .` means “open the current directory in VS Code.” The dot represents the
current directory.

In VS Code, use **Terminal > New Terminal**. Confirm that its prompt ends with:

```text
applied-ai-apprenticeship
```

Do not work from an arbitrary directory. The repository root is the shared
reference point for commands and relative paths.

### Checkpoint 1

Show the output of:

```powershell
Get-Location
python --version
python -c "import sys; print(sys.executable)"
git status
```

What each command proves:

- `Get-Location`: you are inside the intended repository.
- `python --version`: a Python interpreter is available.
- `python -c`: execute the quoted Python statement directly; `sys.executable`
  reveals which interpreter was selected.
- `git status`: shows the repository branch and changed files.

## 3. Create a virtual environment

Run this once from the repository root:

```powershell
python -m venv .venv
```

Breakdown:

- `python` starts the interpreter.
- `-m venv` asks Python to run the standard-library module named `venv`.
- `.venv` is the directory it creates.

The environment contains a project-specific interpreter and a place for this
project's installed packages. Later, FastAPI can use one dependency version
without changing another project's environment.

`.venv` must not be committed. It is generated, machine-specific, and can be
recreated from dependency declarations.

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

Breakdown:

- `.\` means “begin in the current directory.”
- `.venv\Scripts\Activate.ps1` is a PowerShell script created by `venv`.
- Activation changes the current terminal's `PATH` so `python` selects the
  environment's interpreter first.

Activation does not permanently change Python or Windows. It affects this
terminal session. A new terminal must activate the environment again.

Verify it:

```powershell
python --version
python -c "import sys; print(sys.executable)"
python -m pip --version
```

The executable path should contain:

```text
applied-ai-apprenticeship\.venv\Scripts\python.exe
```

`pip` is Python's package installer. We run it as `python -m pip` so it belongs
to the same interpreter selected by `python`. Do not install anything today.

To leave the environment later:

```powershell
deactivate
```

### Checkpoint 2

Send the three verification outputs above. Explain in one sentence why the
second interpreter path differs from the path in Checkpoint 1.

## 4. Create and run the first file

In the VS Code Explorer, create:

```text
projects/learning-tasks-api/scratch/hello_python.py
```

Create missing directories using the Explorer's **New Folder** button. Enter:

```python
print("Hello, Raunak. Python is running.")
```

Save with `Ctrl+S`. From the repository-root terminal, run:

```powershell
python .\projects\learning-tasks-api\scratch\hello_python.py
```

`print` is a built-in Python function. The text inside quotes is a string. The
parentheses contain the argument passed to the function.

Python executes a script from top to bottom. Try:

```python
print("First")
print("Second")
print("Third")
```

Run it again and observe the order.

### Syntax, indentation, and comments

Python uses indentation to define a block:

```python
is_learning = True

if is_learning:
    print("Day 01 is active")
```

The colon begins the block. The four spaces place the `print` statement inside
the `if` statement. VS Code normally inserts four spaces when you press Tab in
a Python file.

A comment begins with `#`:

```python
# This explains why the next line exists.
print("Comments are not executed")
```

Use comments to explain intent or a non-obvious decision. Do not narrate every
obvious line.

### Checkpoint 3

Run `hello_python.py` successfully. Then deliberately remove one closing `)`
and run it again. Read the `SyntaxError`, restore the parenthesis, and confirm
that the file runs again.

## 5. Values, variables, and types

A value is data. A variable is a name bound to a value:

```python
name = "Raunak"
years_of_experience = 3.5
study_hours = 6
is_available = True
current_blocker = None
```

The `=` operator assigns the value on the right to the name on the left. It does
not mean mathematical equality.

Core types for today:

| Type | Example | Meaning |
|---|---|---|
| `str` | `"Python"` | Text |
| `int` | `6` | Whole number |
| `float` | `3.5` | Decimal number |
| `bool` | `True` | Truth value |
| `NoneType` | `None` | Intentional absence of a value |

Inspect them:

```python
print(type(name))
print(type(study_hours))
```

Python is dynamically typed: a name is not permanently restricted to one type.
Our project will still use consistent types and annotations because predictable
code is easier to maintain.

### Naming

Use descriptive `snake_case` names:

```python
completed_task_count = 2
```

Avoid unexplained names such as `x`, `temp`, or `data1`. Names may contain
letters, digits, and underscores, but cannot begin with a digit or use a Python
keyword such as `if` or `for`.

## 6. Operators and expressions

An expression produces a value:

```python
total_hours = 3 + 3
remaining_hours = 7 - 2
double_effort = 4 * 2
average = 15 / 2
whole_result = 15 // 2
remainder = 15 % 2
power = 2 ** 3
```

Comparison operators produce booleans:

```python
print(study_hours >= 6)
print(name == "Raunak")
print(name != "Someone else")
```

- `==` compares values.
- `!=` means not equal.
- `<`, `<=`, `>`, and `>=` compare ordering.

Boolean operators combine conditions:

```python
ready = study_hours >= 6 and is_available
needs_rest = study_hours > 8 or not is_available
```

## 7. Strings

Strings are immutable sequences of characters. “Immutable” means string
contents cannot be changed in place; an operation creates another string.

```python
skill = "python"
display_name = skill.upper()

print(skill)
print(display_name)
print(len(skill))
```

Common operations:

```python
raw_title = "  Learn Python  "
clean_title = raw_title.strip()

print(clean_title.lower())
print(clean_title.startswith("Learn"))
print("Python" in clean_title)
```

Use f-strings to insert values into readable text:

```python
completed = 2
total = 5
print(f"Completed {completed} of {total} tasks")
```

## 8. Lists

A list stores an ordered, mutable collection:

```python
skills = ["Python", "Git", "SQL"]
```

- Ordered: values retain their positions.
- Mutable: values can be added, replaced, or removed.
- Indexes start at zero.

```python
print(skills[0])
print(skills[-1])

skills.append("FastAPI")
skills[1] = "Git and GitHub"
print(len(skills))
```

An index that does not exist raises `IndexError`.

Basic slicing:

```python
print(skills[0:2])
```

The start index is included; the stop index is excluded.

## 9. Dictionaries

A dictionary maps unique keys to values:

```python
learning_task = {
    "title": "Review Python functions",
    "priority": 1,
    "completed": False,
}
```

Read and update values:

```python
print(learning_task["title"])
learning_task["completed"] = True
learning_task["hours"] = 2
```

Direct access raises `KeyError` when the key is missing. `get` can provide a
fallback:

```python
owner = learning_task.get("owner", "Unassigned")
```

A list of dictionaries represents multiple records:

```python
tasks = [
    {"title": "Python syntax", "priority": 1, "completed": True},
    {"title": "Python functions", "priority": 2, "completed": False},
]
```

The list answers “which records exist and in what order?” Each dictionary
answers “which named fields belong to this record?”

## 10. Conditions

Conditions select which block runs:

```python
priority = 1

if priority == 1:
    print("High priority")
elif priority == 2:
    print("Medium priority")
else:
    print("Low priority")
```

Values also have truthiness. Empty strings, empty collections, zero, `False`,
and `None` are falsy. Other ordinary values are truthy.

Write explicit conditions when they improve clarity:

```python
if learning_task["completed"] is False:
    print(learning_task["title"])
```

`is` checks object identity. `is None` and `is not None` are standard. Use `==`
for ordinary value comparison.

## 11. Loops

A `for` loop processes each item from an iterable:

```python
for task in tasks:
    print(task["title"])
```

On every iteration, `task` refers to the next dictionary from `tasks`.

Combine a loop and condition:

```python
for task in tasks:
    if task["completed"] is False:
        print(task["title"])
```

Use `enumerate` when you need a counter:

```python
for position, task in enumerate(tasks, start=1):
    print(f"{position}. {task['title']}")
```

A `while` loop repeats while a condition remains true. Recognize it today, but
the build task only requires `for`:

```python
count = 0

while count < 3:
    print(count)
    count += 1
```

## 12. Functions

A function gives a named operation a clear boundary:

```python
def format_greeting(name: str) -> str:
    message = f"Hello, {name}"
    return message
```

Breakdown:

- `def` begins a function definition.
- `format_greeting` is the function name.
- `name` is a parameter.
- `: str` documents the expected argument type.
- `-> str` documents the return type.
- `return` sends a result back to the caller.

Calling it:

```python
greeting = format_greeting("Raunak")
print(greeting)
```

`print` displays something for a person. `return` gives a value to other code.
A function that only prints is harder to reuse and test than one that returns a
result.

A function with no useful returned value uses `-> None`:

```python
def show_heading(title: str) -> None:
    print(f"=== {title} ===")
```

Parameters exist only inside their function. Variables created in a function
are local variables.

## 13. Type hints

Type hints describe the intended shapes of values:

```python
def count_completed(tasks: list[dict[str, object]]) -> int:
    completed_count = 0

    for task in tasks:
        if task["completed"] is True:
            completed_count += 1

    return completed_count
```

Read the signature aloud:

> `count_completed` receives a list of dictionaries. Each dictionary has string
> keys and values that may be different object types. It returns an integer.

Python does not normally reject a bad argument merely because of a type hint.
Pylance, type checkers, and frameworks such as FastAPI use these annotations to
understand the program. Later we will replace broad `object` values with more
precise models.

## 14. The main guard

Python assigns the special name `__name__` to every module. When a file is run
directly, its value is `"__main__"`:

```python
def main() -> None:
    print("Program started")


if __name__ == "__main__":
    main()
```

This keeps program startup separate from reusable functions. When another file
imports this module later, `main()` will not run automatically.

Use two blank lines between top-level function definitions. VS Code and future
formatting tools will help enforce conventional Python style.

## 15. Errors and tracebacks

Three categories matter today:

- `SyntaxError`: Python could not understand the source code.
- Runtime exception: syntax was valid, but execution failed.
- Logic error: the program ran, but produced the wrong result.

Example runtime exception:

```python
numbers = [10, 20]
print(numbers[5])
```

Read a traceback from the bottom upward:

1. The final line gives the exception type and message.
2. The preceding file and line number identify where it happened.
3. Inspect the values and assumption on that line.

Do not randomly change code. State what you expected, what actually occurred,
and which assumption was false.

## 16. VS Code workflow

### Select the interpreter

After `.venv` exists:

1. Press `Ctrl+Shift+P`.
2. Search for `Python: Select Interpreter`.
3. Choose the interpreter containing `.venv\Scripts\python.exe`.

The bottom status bar should indicate the selected Python environment.

### Run from the terminal

The terminal is our primary method because its behavior is explicit and will
transfer to servers, Docker containers, and continuous-integration systems:

```powershell
python .\path\to\file.py
```

### Run with the debugger

1. Open a Python file.
2. Click beside a line number to add a red breakpoint.
3. Press `F5`.
4. Choose `Python File` if prompted.
5. Inspect variables, use Step Over, and continue execution.

A breakpoint pauses before a line executes. Debugging lets you observe the
program state instead of guessing.

## 17. Main build task

Now create:

```text
projects/learning-tasks-api/scratch/day_01_task_summary.py
```

Implement the requirements in `brief.md` using this sequence:

1. Create a list containing at least three task dictionaries.
2. Print the raw list once and inspect its shape.
3. Write a function that prints only incomplete tasks.
4. Call the function and verify its output.
5. Write a function that searches by title and marks the matching task complete.
6. Decide what useful result that function should return when it succeeds and
   when no title matches.
7. Write a function that calculates the completed count.
8. Print a readable final summary using an f-string.
9. Add type hints to every function.
10. Put startup code in `main()` and call it with the main guard.

Do not optimize early. Make one small change, save it, run the file, and inspect
the output. That edit-run-observe loop is the core development habit.

### Manual cases to check

- Initially, only incomplete tasks are printed.
- Marking an existing title changes exactly one task.
- Searching for an unknown title returns your documented failure result and
  does not crash.
- The total count equals the list length.
- The completed count matches the final task data.

## 18. Written practice

Create the notes file required by `brief.md`. Write from memory first. Then
compare your explanation with this lesson and correct anything inaccurate.

## 19. Inspect and commit

Before committing:

```powershell
git status
git diff
```

- `git status` shows untracked, modified, and staged paths.
- `git diff` shows unstaged line changes.

Make sure `.venv` is not listed. Stage only today's intended files:

```powershell
git add .\projects\learning-tasks-api\scratch\day_01_task_summary.py
git add .\projects\learning-tasks-api\notes\day-01-python-foundations.md
git add .\days\day-01\review.md
```

Inspect the staged snapshot:

```powershell
git diff --staged
```

Commit it:

```powershell
git commit -m "feat: add day 01 Python foundations"
git push origin main
```

- A commit is a named local snapshot.
- A push sends local commits to the remote GitHub repository.
- The commit message states what the snapshot adds.

Do not commit until the script runs, the output is checked, and your reflection
is honest.

## 20. Final evidence

Submit:

- the GitHub commit link;
- the complete terminal command used to run the script;
- the script output;
- what you built;
- what failed and why;
- one lesson;
- any blocker;
- actual focused hours.

The mentor review will inspect correctness, naming, function boundaries, type
hints, output, and your ability to explain the code.
