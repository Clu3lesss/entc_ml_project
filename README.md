# Spotify Cluster Predictor

## Backend API

Install the Python dependencies from the repository root:

```powershell
python -m pip install -r requirements.txt
python -m uvicorn main:app --app-dir api --reload
```

The API runs at `http://127.0.0.1:8000`. Check `http://127.0.0.1:8000/health`
to verify it has loaded the model and dataset.

## React frontend

In a second terminal:

```powershell
cd frontend
npm ci
npm run dev
```

Open the Vite URL printed in the terminal. The frontend sends API requests to
`http://localhost:8000`.

## Project folders

- `api/` — FastAPI application
- `frontend/` — React application and Vite configuration
- `data/` — Spotify track datasets
- `models/` — trained model and parameters
- `notebooks/` — analysis and feature-engineering notebooks
- `scripts/` — model training, tuning, and prediction tools
