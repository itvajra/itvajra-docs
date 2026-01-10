# Local Development

## Frontend

```
cd policyhq-frontend
npm install
npm run dev
```

Defaults:

- Dev server: `http://localhost:5173`
- API base URL: `http://localhost:8000/api` (override with `VITE_API_BASE_URL`)

## Backend

```
cd policyhq-backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

## Local storage for exports

If `DEBUG` is true and Azure Blob credentials are placeholders, exports are written to:

```
policyhq-backend/storage/<azure_blob_container>/
```

In this mode, downloads are served from `/api/static-exports/...`.
