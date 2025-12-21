# Setup and Development

This document lists commands to run the frontend and model API for development.

Prerequisites
- Node.js (18+ recommended) and `npm` (or `pnpm`/`yarn`) for the frontend.
- Python 3.10 for the model API (the Docker image uses 3.10-slim).
- Docker (optional) if you prefer containerized model service.

Frontend (development)

```bash
cd frontend
npm install
npm run dev
# opens on http://localhost:3000
```

Frontend (build)

```bash
cd frontend
npm install
npm run build
npm start
```

Model API (local Python)

```bash
cd model-lab
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
# run from repo root or inside model-lab as described in README
uvicorn app.main:app --reload --host 0.0.0.0 --port 8080
```

Model API (Docker)

```bash
docker build -t sentiment-model -f model-lab/Dockerfile model-lab
docker run -p 8080:8080 sentiment-model
```

Notes
- The FastAPI app configures CORS; by default the frontend origin is `http://localhost:3000`.
- The ONNX model used is at `model-lab/models/onxx_models/emotion-ferplus-8.onnx`.
