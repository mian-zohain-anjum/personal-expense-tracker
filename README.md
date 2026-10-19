# personal-expense-tracker
virtual environment

# Personal Expense Tracker

A beginner-friendly Python command-line application for recording, reviewing, and summarizing personal expenses. The project is designed to teach core Python programming alongside a professional development workflow using a virtual environment, Git, GitHub, and automated tests.

## Project goals

- Record an expense with an amount, category, description, and date.
- Display saved expenses.
- Calculate total spending and spending by category.
- Filter expenses by category or date.
- Delete an expense.
- Persist data between runs using JSON.
- Validate user input and handle common errors safely.
- Add automated tests and maintain readable, well-structured code.

## Planned technology

- **Python:** 3.12 or later recommended
- **Storage:** JSON using Python's standard library
- **Environment:** `venv`
- **Testing:** `pytest`
- **Code quality:** `ruff`
- **Version control:** Git and GitHub

The initial version does not require a database or a web framework. SQLite can be added as a future enhancement.

## Planned project structure

```text
expense-tracker/
├── .venv/                      # Local virtual environment; never commit
├── src/
│   └── expense_tracker/
│       ├── __init__.py
│       ├── main.py             # CLI menu and application entry point
│       ├── expense.py          # Expense model and business rules
│       └── storage.py          # JSON read/write operations
├── tests/
│   ├── test_expense.py
│   └── test_storage.py
├── data/
│   └── expenses.json           # Local user data; normally ignored by Git
├── .gitignore
├── README.md
├── requirements.txt
└── pyproject.toml
```

This structure is a planned layout; files can be added as each feature is implemented.

## Setup

### 1. Check Python and Git

```bash
python --version
git --version
```

If your system uses `python3` instead of `python`, substitute `python3` in the commands below.

### 2. Create and enter the project

```bash
mkdir expense-tracker
cd expense-tracker
git init
```

### 3. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

**Windows PowerShell**
```powershell
.venv\Scripts\Activate.ps1
```

**Windows Command Prompt**
```bat
.venv\Scripts\activate.bat
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

### 4. Install development tools

```bash
python -m pip install pytest ruff
```

Once the project has dependencies, record them with:

```bash
python -m pip freeze > requirements.txt
```

To install recorded dependencies later:

```bash
python -m pip install -r requirements.txt
```

## Usage

The application commands and menu will be documented here as they are implemented. The intended workflow is:

1. Start the CLI application.
2. Choose an action from the menu.
3. Enter expense details.
4. Review the saved expenses or summary.
5. Exit; data remains saved in the JSON file.

## Development workflow

Make one small, working change at a time. Example commit messages:

```text
chore: initialize Python project
feat: add expense model
feat: save expenses to JSON
feat: add expense summary
test: cover expense validation
docs: document setup and usage
```

Useful commands:

```bash
# Run tests
python -m pytest -v

# Check code
python -m ruff check .

# Format code
python -m ruff format .
```

## Git ignore

Create `.gitignore` and include at least:

```gitignore
.venv/
__pycache__/
*.py[cod]
.pytest_cache/
.ruff_cache/
.mypy_cache/
.env
.vscode/
.idea/
.DS_Store
Thumbs.db
```

If `data/expenses.json` contains real personal information, add that exact path to `.gitignore`. You may commit a separate sanitized sample file instead. Do not commit private financial records.

## Testing plan

Tests should cover:

- Valid expense creation.
- Invalid, zero, or negative amounts.
- Empty descriptions and invalid dates.
- Correct total and category calculations.
- Saving and loading JSON data.
- Missing or empty data files.
- Malformed JSON and filesystem errors.
- Deleting an expense that exists and handling an unknown ID.

Use temporary directories and sample data in tests; never test against real personal expense records.

## Roadmap

1. Create the project structure and Git repository.
2. Implement the expense model and input validation.
3. Implement JSON persistence.
4. Build the CLI menu and add/list/delete actions.
5. Add total and category summaries.
6. Add filtering by category and date.
7. Write tests and apply Ruff.
8. Complete the README and publish the repository on GitHub.
9. Optional: migrate storage to SQLite or add CSV export.

## Learning resources

- [Python Tutorial](https://docs.python.org/3/tutorial/)
- [Python `venv`](https://docs.python.org/3/library/venv.html)
- [Python `json`](https://docs.python.org/3/library/json.html)
- [Pro Git book](https://git-scm.com/book/en/v2)
- [GitHub: Get started](https://docs.github.com/en/get-started/start-your-journey)
- [pytest documentation](https://docs.pytest.org/en/stable/)
- [Ruff documentation](https://docs.astral.sh/ruff/)

## Scope and limitations

This is an educational, local CLI project, not a financial or accounting system. It will not connect to bank accounts, process payments, or provide financial advice. Data is stored locally, so users are responsible for backups and protecting their files.
