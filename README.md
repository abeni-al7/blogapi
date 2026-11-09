# Blog API

A REST API for a blog, built with Django and Django REST Framework. Users register and log in through dj-rest-auth, and only authenticated users can use the API.

## Features

- `Post` model: `title`, `body`, `author` (a user), `created_at`, `updated_at`
- Custom user model (`accounts.CustomUser`) with an optional `name` field
- Permissions: any logged-in user can read posts, but only a post's author can edit or delete it. Only admins can access the users endpoints.
- Session and token authentication
- OpenAPI schema generated with drf-spectacular, with Swagger UI and ReDoc pages
- CORS allowed for `localhost:3000` and `localhost:8000`

## API

| Path | Description |
| --- | --- |
| `/api/v1/` | List and create posts |
| `/api/v1/<id>/` | Retrieve, update or delete a post |
| `/api/v1/users/`, `/api/v1/users/<id>/` | Users (admin only) |
| `/api/v1/dj-rest-auth/` | Login, logout, password endpoints (dj-rest-auth) |
| `/api/v1/dj-rest-auth/registration/` | Sign up |
| `/api-auth/` | DRF browsable API login |
| `/api/schema/`, `/api/schema/swagger-ui/`, `/api/schema/redoc/` | OpenAPI schema and docs |
| `/admin/` | Django admin |

## Built with

Python, Django 5.1, Django REST Framework, dj-rest-auth, django-allauth, drf-spectacular, django-cors-headers, environs, WhiteNoise, Gunicorn, PostgreSQL (psycopg2).

## Run it

Set these environment variables (a `.env` file is read automatically):

- `SECRET_KEY` (required)
- `DATABASE_URL` (required)
- `DEBUG` (optional, defaults to `False`)

```sh
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

`render.yaml` and `build.sh` deploy the app to Render with a free PostgreSQL database, running `gunicorn django_project.wsgi`.
