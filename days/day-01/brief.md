# Day 1 - Python API Environment and Health Check

Estimated focused time: 5-6 hours

## Main build task

Set up a Python 3.12 virtual environment and build a minimal FastAPI service in `projects/learning-tasks-api`.

The service must expose `GET /health` and return status code `200` with this exact JSON body:

```json
{
  "status": "ok",
  "service": "learning-tasks-api"
}
```

Create one automated test that proves the endpoint returns this status code and JSON body.

## Constraints

- Create every source file yourself. Do not copy a complete tutorial application.
- You may use FastAPI and pytest official documentation as references.
- Install only: `fastapi`, `uvicorn[standard]`, `pytest`, and `httpx`.
- Add the installed packages to `requirements.txt` yourself, with an explanation in the README of why each package exists.
- Keep application code in an `app` package and tests in a `tests` package.

## Suggested command sequence

Run these from `projects/learning-tasks-api` in a new PowerShell terminal:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install fastapi "uvicorn[standard]" pytest httpx
```

If PowerShell blocks activation, report the exact error. Do not change execution policy without discussing it first.

## Small practice task

Create `projects/learning-tasks-api/notes/day-01-python-foundations.md`. In your own words, explain:

1. Why a virtual environment exists.
2. What an ASGI application is at a practical level.
3. Why API tests are useful even for one endpoint.
4. The difference between a Python module and a package.
5. One mistake you made today and how you corrected it.

## Done criteria

- `pytest` passes.
- `uvicorn` starts locally and `/health` returns the exact JSON body.
- `requirements.txt` is complete.
- README contains setup, run, and test commands.
- Notes are written in your own words.
- One Git commit is created with a message such as `feat: add FastAPI health endpoint`.

## Evening review submission

Complete `days/day-01/review.md`, commit your work, push to GitHub, then send me the commit link.
