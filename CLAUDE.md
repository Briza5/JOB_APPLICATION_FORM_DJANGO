# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Django 6 web app — job application form. Course project from The Python Mega Course (Sections 49–51), reimplementing a prior Flask/MySQL project using Django's built-in ORM, admin panel, and form handling. Virtual environment is in `.venv/`.

## Commands

```bash
# Activate venv (Windows)
.venv\Scripts\activate

# Run development server
python manage.py runserver

# Create and apply migrations after model changes
python manage.py makemigrations
python manage.py migrate

# Create admin superuser
python manage.py createsuperuser

# Run tests
python manage.py test
python manage.py test job_application   # single app
```

## Architecture

Two-package layout: `mysite/` is the project config (settings, root URLs), `job_application/` is the only Django app.

```
mysite/settings.py   — INSTALLED_APPS, DB (SQLite), email config
mysite/urls.py       — root URL router, includes job_application URLs
job_application/
    models.py        — DB schema (Form model → db.sqlite3)
    views.py         — request handling logic
    forms.py         — Django ModelForm (to be added)
    admin.py         — admin panel registration
    urls.py          — app-level URL patterns (to be added)
    templates/       — HTML templates (to be added)
```

Django request flow: URL match in `mysite/urls.py` → delegates to `job_application/urls.py` → view function in `views.py` → renders template → saves via ORM model.

## Key conventions in this project

- Database: SQLite (`db.sqlite3`) — do not switch to another engine without updating `INSTALLED_APPS` and running fresh migrations.
- After any change to `models.py`, always run `makemigrations` then `migrate`.
- New apps must be added to `INSTALLED_APPS` in `mysite/settings.py` before migrations will work.
- Admin panel at `/admin/` — models must be registered in `job_application/admin.py` to appear there.
- `NOTES.md` is excluded from git (course documentation only).
