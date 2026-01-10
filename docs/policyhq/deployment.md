# Deployment

## Docker

Both frontend and backend include Dockerfiles:

- Frontend: `policyhq-frontend/Dockerfile`
- Backend: `policyhq-backend/Dockerfile`

Backend container exposes port 8000 and includes a health check on `/health`.

## Environment configuration

Set environment variables for:

- Database connection (`DATABASE_URL`)
- Azure storage (`AZURE_BLOB_CONNECTION_STRING`, `AZURE_BLOB_CONTAINER`)
- Entra ID config (see `policyhq-backend/app/auth/entra_config.py`)
- Email provider configuration
- CORS origins and app URLs

## Static hosting

The frontend is a Vite app and can be deployed to any static host. It expects the API URL from `VITE_API_BASE_URL`.
