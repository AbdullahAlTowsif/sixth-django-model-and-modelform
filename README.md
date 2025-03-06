# Django Migrations

Django migrations are a way of propagating changes to your database schema. They allow you to manage database evolution in a structured and version-controlled manner.

## Table of Contents
- [Introduction](#introduction)
- [Creating Migrations](#creating-migrations)
- [Applying Migrations](#applying-migrations)
- [Checking Migration Status](#checking-migration-status)
- [Rolling Back Migrations](#rolling-back-migrations)
- [Handling Conflicts](#handling-conflicts)
- [Creating a Superuser](#creating-a-superuser)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

---

## Introduction
Migrations track changes to Django models and apply them to the database. They are stored as Python files inside the `migrations` directory of each Django app.

## Creating Migrations
After making changes to your models, create a migration file by running:

```bash
python manage.py makemigrations
```

This will generate a migration script inside your app's `migrations/` directory.

## Applying Migrations
Apply migrations to the database with:

```bash
python manage.py migrate
```

This applies all unapplied migrations in the correct order.

## Checking Migration Status
To check which migrations have been applied:

```bash
python manage.py showmigrations
```

## Rolling Back Migrations
To undo a specific migration (e.g., `0003_auto`), run:

```bash
python manage.py migrate app_name 0002
```

This reverts the app's migrations to the specified state.

## Handling Conflicts
If multiple developers create migrations that conflict, resolve them by running:

```bash
python manage.py makemigrations --merge
```

## Creating a Superuser
To create a superuser (admin account) for Django’s admin panel, run:

```bash
python manage.py createsuperuser
```

You will be prompted to enter a username, email, and password. Once created, log in to the Django admin panel at:

```
http://127.0.0.1:8000/admin/
```

## Best Practices
- Always run `makemigrations` before committing model changes.
- Use `squashmigrations` to optimize migration history.
- Keep backups before rolling back migrations.
- Use `inspectdb` to generate models from an existing database.

## Troubleshooting
- If migrations are not detected, check `INSTALLED_APPS` for missing apps.
- If `migrate` fails, try `python manage.py migrate --fake-initial` for existing databases.
- Clear migration files (except `__init__.py`), run `makemigrations` and `migrate` to reset.

For more details, refer to the [Django documentation](https://docs.djangoproject.com/en/stable/topics/migrations/).

