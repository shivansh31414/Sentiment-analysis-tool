# Sentiment Analysis Tool

Small web app that predicts facial emotions from images using an ONNX model and a Next.js frontend.

Key pieces
- Frontend: `frontend/` — Next.js app (TypeScript) serving the UI and demo at `/demo`.
- Model API: `model-lab/` — FastAPI app that loads `models/onxx_models/emotion-ferplus-8.onnx` and exposes a `/predict` endpoint.

Quick start (frontend)

```bash
cd frontend
npm install
npm run dev
# open http://localhost:3000
```

Quick start (model API, local Python)

```bash
cd model-lab
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
# from project root (recommended):
uvicorn app.main:app --reload --host 0.0.0.0 --port 8080
# or if you're inside model-lab/app:
uvicorn main:app --reload --host 0.0.0.0 --port 8080
# API will be available at http://localhost:8080
```

Quick start (model API, with Docker)

```bash
docker build -t sentiment-model -f model-lab/Dockerfile model-lab
docker run -p 8080:8080 sentiment-model
# API will be available at http://localhost:8080
```

Usage
- Demo UI: http://localhost:3000/demo
- API: `POST /predict` with multipart `file` (image) and optional `model_option` form field.

More detailed developer instructions are in the `docs/` folder.
