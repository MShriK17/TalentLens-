# TalentLens Deployment Guide

This repository contains:

- `backend/` — FastAPI backend service
- `frontend/` — React frontend (Create React App + CRACO)
- `render.yaml` — Render deployment configuration for the backend
- `frontend/vercel.json` — Vercel deployment configuration for the frontend
- `.github/workflows/ci.yml` — CI workflow for backend validation and frontend build checks

## Recommended deployment

- **Backend**: Render
- **Frontend**: Vercel

## Backend deployment on Render

1. Create a new Python Web Service on Render.
2. Connect your GitHub repo: `https://github.com/MShriK17/TalentLens-.git`
3. Render will automatically use `render.yaml`.
4. Add these environment variables in Render:
   - `MONGO_URL`
   - `DB_NAME`
   - `MAIL_USERNAME`
   - `MAIL_PASSWORD`
   - `MAIL_FROM`
   - `MAIL_SERVER`
   - `MAIL_PORT`
5. Set the `buildCommand` to:
   - `pip install -r backend/requirements.txt`
6. Set the `startCommand` to:
   - `uvicorn backend.server:app --host 0.0.0.0 --port ${PORT}`

## Frontend deployment on Vercel

1. Create a new project in Vercel.
2. Select this GitHub repo.
3. Set the project root to `frontend`.
4. Use the default install command (`npm install`) and build command (`npm run build`).
5. Output directory should be `build`.
6. Ensure `frontend/vercel.json` is present in the frontend folder.

## Local development

### Backend

```bash
cd backend
python -m pip install -r requirements.txt
uvicorn server:app --host 127.0.0.1 --port 8000
```

### Frontend

```bash
cd frontend
npm install
npm start
```

## Notes

- The backend uses MongoDB and expects `MONGO_URL`/`DB_NAME` to be configured.
- The backend also supports email via SMTP when the mail env vars are set.
- CI automatically checks backend syntax and builds the frontend on every push.
