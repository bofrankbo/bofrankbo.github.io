# Repository Guidelines

## Project Structure & Module Organization

This repository has a small GitHub Pages entry point at `index.html` and a Flask application in `My-Website-Azure-main/`.

- `My-Website-Azure-main/app.py` starts the Flask app and registers routes.
- `My-Website-Azure-main/modules/` contains Python modules for routes, database CSV handling, OCR, configuration, and utilities.
- `My-Website-Azure-main/templates/` stores Jinja HTML templates; demo pages live in `templates/demo/`.
- `My-Website-Azure-main/static/` stores CSS, JavaScript, favicons, and images.
- `My-Website-Azure-main/data/` contains CSV data and sample upload images used by the demo flows.
- `My-Website-Azure-main/.github/workflows/main_frankwebjp.yml` builds and deploys the Python app to Azure on pushes to `main`.

## Build, Test, and Development Commands

Run commands from `My-Website-Azure-main/` unless noted.

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

The app runs locally on `http://localhost:5001` with debug mode enabled. The Azure workflow uses Python 3.11 and installs dependencies with `pip install -r requirements.txt`.

There is currently no build step for the static root `index.html`.

## Coding Style & Naming Conventions

Use standard Python style: 4-space indentation, descriptive `snake_case` function names, and route handlers grouped in `modules/routes.py`. Keep reusable logic in `modules/utils.py`, `modules/database.py`, or another focused module instead of placing it directly in `app.py`.

Templates use lowercase filenames and the existing `demo_<page>.html` pattern. Static assets should stay in the relevant `static/css/`, `static/js/`, or `static/assets/` folder.

## Testing Guidelines

No automated tests are currently present. For Python changes, add tests under `My-Website-Azure-main/tests/` using `pytest` when introducing logic that can regress, especially CSV import/export, route behavior, and OCR parsing helpers. Name test files `test_<module>.py` and test functions `test_<behavior>()`.

Until tests exist, manually verify key routes after `python app.py`: `/`, `/contact`, `/demo/client`, `/demo/passport`, and `/demo/trip`.

## Commit & Pull Request Guidelines

The current Git history uses brief imperative commit messages such as `Update index.html` and `Create index.html`. Continue with concise, action-oriented messages, for example `Add client CSV validation`.

Pull requests should include a short summary, manual test notes, screenshots for visible UI changes, and any Azure deployment or configuration impact. Do not commit secrets, local virtual environments, `__pycache__/`, or generated deployment archives.

## Security & Configuration Tips

Avoid hardcoding credentials in route or auth modules. Move secrets to environment variables or Azure App Service settings, and keep production values out of source control.


# language
only english in my web page