# Job Application Form — Django

> 🇬🇧 English version below / 🇨🇿 Česká verze níže

---

## 🇬🇧 English

### Description

A Django web application for collecting job applications. Users fill out a form with their personal details and availability, the data is saved to a SQLite database, and a confirmation email is sent to the applicant. The project reimplements a prior Flask/MySQL app using Django's built-in ORM, admin panel, and email framework.

### Features

- Job application form with Bootstrap UI
- CSRF protection via Django middleware
- Form validation via Django `forms.Form`
- Data persistence to SQLite via Django ORM
- Confirmation email sent via Gmail SMTP
- Flash messages for user feedback
- Django admin panel with search, filters, and ordering
- Base template with responsive Bootstrap navbar inherited across all pages

### How to Run

```bash
# 1. Create and activate virtual environment
python -m venv .venv
.venv\Scripts\activate       # Windows

# 2. Install dependencies
pip install -r requirements.txt

# 3. Apply migrations
python manage.py migrate

# 4. Create admin superuser
python manage.py createsuperuser

# 5. Set Gmail credentials (required for email sending)
# Windows PowerShell:
$env:PASSWORD = "your_app_password"

# 6. Start the development server
python manage.py runserver
```

Open `http://127.0.0.1:8000/` for the form, `/admin/` for the admin panel.

### Project Structure

```
JOB_APPLICATION_FORM_DJANGO/
├── manage.py
├── requirements.txt
├── db.sqlite3
├── mysite/
│   ├── settings.py        # DB, email backend, INSTALLED_APPS
│   └── urls.py            # root URL router
└── job_application/
    ├── models.py          # Form model → SQLite table
    ├── forms.py           # ApplicationForm → POST validation
    ├── views.py           # index + about views
    ├── urls.py            # URL patterns
    ├── admin.py           # FormAdmin — customized admin interface
    ├── migrations/
    └── templates/
        ├── base.html      # shared Bootstrap layout + navbar
        ├── index.html     # application form page
        └── about.html     # about page
```

### Key Concepts Practiced

- Django MTV architecture (Model–Template–View)
- ORM model definition and database migrations
- Django form validation with `cleaned_data`
- Template inheritance with `{% extends %}` and `{% block %}`
- Django admin customization via `ModelAdmin`
- Flash messages with `django.contrib.messages`
- Email sending via `django.core.mail.EmailMessage`
- Secure credential handling with `os.getenv()`

---

## 🇨🇿 Česky

### Popis

Django webová aplikace pro sběr pracovních přihlášek. Uživatel vyplní formulář s osobními údaji a dostupností, data se uloží do SQLite databáze a žadateli přijde potvrzovací e-mail. Projekt reimplementuje předchozí Flask/MySQL aplikaci s využitím Django ORM, admin panelu a emailového frameworku.

### Funkce

- Formulář pro pracovní přihlášku s Bootstrap UI
- CSRF ochrana přes Django middleware
- Validace formuláře přes Django `forms.Form`
- Ukládání dat do SQLite přes Django ORM
- Potvrzovací e-mail odeslaný přes Gmail SMTP
- Flash zprávy pro zpětnou vazbu uživateli
- Django admin panel s vyhledáváním, filtry a řazením
- Base šablona s responzivním Bootstrap navbarem děděným na všech stránkách

### Jak spustit

```bash
# 1. Vytvoř a aktivuj virtuální prostředí
python -m venv .venv
.venv\Scripts\activate       # Windows

# 2. Nainstaluj závislosti
pip install -r requirements.txt

# 3. Aplikuj migrace
python manage.py migrate

# 4. Vytvoř admin superusera
python manage.py createsuperuser

# 5. Nastav Gmail přihlašovací údaje (nutné pro odesílání e-mailů)
# Windows PowerShell:
$env:PASSWORD = "tvoje_app_heslo"

# 6. Spusť vývojový server
python manage.py runserver
```

Formulář: `http://127.0.0.1:8000/` | Admin panel: `/admin/`

### Klíčové koncepty

- Django MTV architektura (Model–Template–View)
- Definice ORM modelu a databázové migrace
- Validace formuláře přes `cleaned_data`
- Dědičnost šablon přes `{% extends %}` a `{% block %}`
- Přizpůsobení Django adminu přes `ModelAdmin`
- Flash zprávy s `django.contrib.messages`
- Odesílání e-mailů přes `django.core.mail.EmailMessage`
- Bezpečná práce s hesly přes `os.getenv()`
