# KrishiMitra

A local Flask crop-diversification information app for Vidarbha. The project includes a Random Forest model, frontend, API, SQLite/MySQL database adapter, schema, and tests.

## Run on Windows

Requirements: Windows 10/11, 64-bit Python 3.12, and internet access for the first package installation. Node.js and MySQL are not required for the default SQLite setup.

1. Download this repository as a ZIP and extract it, or clone it with Git.
2. Open the extracted `KrishiMitra-GitHub-Ready` folder in VS Code.
3. Double-click `run-transfer.bat`, or run these commands in PowerShell from the project folder:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install --upgrade pip
.\.venv\Scripts\python.exe -m pip install -r requirements-transfer.txt
.\.venv\Scripts\python.exe -m backend.app
```

4. Open http://127.0.0.1:5000 and leave the terminal window open while using the app. Press Ctrl+C in that window to stop it.

The first launch creates a local SQLite database at `instance/krishimitra.db` and a local session key. Those machine-specific files are intentionally not committed; the schema is in `database/sqlite_schema.sql` and initializes automatically. The saved model is `ml/models/random_forest.joblib`.

## Optional configuration

SQLite is the default and requires no `.env` file or credentials. Copy `.env.example` to `.env` only if you need to customize settings. Never commit `.env`, passwords, or API tokens. MySQL is optional; configure it only when you have a local MySQL database and credentials.

## Project folders

- `backend/` Flask app, routes, database adapter, and services
- `frontend/` HTML, CSS, JavaScript, and crop images
- `database/` SQLite and MySQL schema files
- `ml/` training/evaluation code, data, metrics, and saved model
- `tests/` automated tests
- `docs/` project documentation and screenshots
- `scripts/` setup and utility scripts
- `instance/` local runtime data (created on first run; not committed)

The included recommendation training dataset is documented in `ml/data/README.md`. The model's published evaluation details and limitations are in `ml/models/metrics.json` and the project documentation. It should not be interpreted as verified farm-outcome accuracy.

## Retrain the model

After installing dependencies, run:

```powershell
.\.venv\Scripts\python.exe -m ml.train_model
```

Retraining updates the saved model and metrics in the project. Keep a backup if you want to preserve the included model.
