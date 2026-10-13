# Spotify Cluster Predictor

Explore Spotify tracks through audio-feature clustering, predict a track's
mood cluster, and discover similar songs.

## Live application

- **Frontend:** [SoundCluster on Vercel](https://musicluster-98zb1v23i-titanxtreme.vercel.app/)
- **Backend API:** [Spotify Cluster Predictor on Render](https://entc-ml-project.onrender.com/)
- **API health check:** [Check backend status](https://entc-ml-project.onrender.com/health)

## Features

- Explore Spotify audio-feature clusters and their mood profiles.
- Predict the cluster for a track using its audio features.
- Search tracks and get similar-song suggestions by mood or seed songs.
- Use the API independently through its interactive OpenAPI documentation at
  [`/docs`](https://entc-ml-project.onrender.com/docs).

## Technology

- **Frontend:** React, Vite, and Recharts
- **Backend:** Python, FastAPI, scikit-learn, and pandas
- **Deployment:** Vercel (frontend) and Render (API)

## Run locally

### 1. Start the backend

From the repository root, install the Python dependencies and launch the API:

```powershell
python -m pip install -r backend/requirements.txt
python -m uvicorn main:app --app-dir backend/api --reload
```

The API is available at `http://localhost:8000`. Check
`http://localhost:8000/health` to confirm that the model and dataset loaded.

### 2. Start the frontend

In a second terminal, configure the API URL and run the Vite development
server:

```powershell
cd frontend
Copy-Item .env.example .env.local
npm ci
npm run dev
```

The example `.env.local` points to `http://localhost:8000`. Update
`VITE_API_URL` there if the backend uses a different address. Open the local
URL printed by Vite.

To create a production frontend build, run `npm run build` from `frontend/`.

## API endpoints

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `GET` | `/health` | Backend health and model status |
| `GET` | `/clusters` | Cluster labels and descriptions |
| `GET` | `/stats` | Dataset statistics |
| `GET` | `/songs/search` | Search tracks by name or artist |
| `POST` | `/predict` | Predict a track's cluster |
| `POST` | `/suggest` | Recommend similar tracks |

Interactive API documentation is served at `/docs` when the backend is running.

## Repository layout

```text
backend/
  api/          FastAPI application
  data/         Spotify track datasets
  models/       Trained clustering model and parameters
  notebooks/    Data exploration and feature engineering
  scripts/      Model training, tuning, and prediction tools
  requirements.txt
frontend/
  src/          React application
  public/       Static assets
  .env.example  Local API URL configuration
```

For more detail, see the [backend guide](backend/README.md) and
[frontend guide](frontend/README.md).
