# Backend (policyhq-backend)

The backend is a FastAPI service with SQLAlchemy models and Entra ID token validation.

## Tech stack

- FastAPI
- SQLAlchemy 2.x
- Pydantic settings
- python-jose for JWT validation
- Azure Blob Storage SDK
- ReportLab and python-docx for exports

## App entry point

- Main app: `policyhq-backend/app/main.py`
- OpenAPI docs: `/api/docs` and `/api/redoc`
- Health check: `/health`

## Database

- Engine configured in `policyhq-backend/app/database.py`
- Models in `policyhq-backend/app/models/`
- Multi-tenancy enforced via `TenantContext` derived from token claims and DB mapping

## Services

- Policy generation: `app/services/generation_service.py`
- Exports: `app/services/export_service.py`
- Azure storage: `app/services/blob_service.py`
- Email: `app/services/email_service.py`

## Local development

```
cd policyhq-backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

## Environment variables

Configured in `policyhq-backend/app/config.py` and `policyhq-backend/app/auth/entra_config.py`.

Core settings:

- `DATABASE_URL`
- `AZURE_BLOB_CONNECTION_STRING`
- `AZURE_BLOB_CONTAINER`
- `DEBUG`
- `CORS_ORIGINS`
- `DEFAULT_CLIENT_ORG_ID`
- `EXPORT_URL_EXPIRY_HOURS`

Email settings:

- `EMAIL_PROVIDER` (smtp, azure_communication, sendgrid)
- `EMAIL_FROM_ADDRESS`
- `EMAIL_FROM_NAME`
- `APP_URL`
- `AZURE_COMMUNICATION_CONNECTION_STRING`
- `SENDGRID_API_KEY`
- `SMTP_HOST`
- `SMTP_PORT`
- `SMTP_USERNAME`
- `SMTP_PASSWORD`
- `SMTP_USE_TLS`

AI provider settings:

- `AI_PROVIDER` (mock, openai, azure_openai)
- `OPENAI_API_KEY`
- `AZURE_OPENAI_ENDPOINT`
- `AZURE_OPENAI_API_KEY`
- `AZURE_OPENAI_DEPLOYMENT`
