# Project Architecture

Overview

This repository contains two primary parts:

- Frontend (`frontend/`): Next.js application that provides the UI and a small demo at `/demo`.
- Model service (`model-lab/`): FastAPI-based Python service that loads an ONNX emotion detection model and exposes a `POST /predict` endpoint.

Key files and responsibilities

- `frontend/` — Next.js app and UI components in `frontend/components` and `frontend/app`.
- `model-lab/app/main.py` — FastAPI app; accepts multipart image uploads and returns predicted emotion and probabilities.
- `model-lab/app/model.py` — Model wrapper that loads the ONNX model and exposes a `predict()` method.
- `model-lab/models/onxx_models/emotion-ferplus-8.onnx` — The ONNX emotion recognition model file.
- `model-lab/Dockerfile` — Container image for the model service (runs Uvicorn on port 8080).

Runtime flow

1. User uploads an image via the frontend (or `curl`).
2. Frontend sends a multipart `POST` to `http://<model-host>:8080/predict`.
3. FastAPI endpoint validates the image, instantiates `Model(model_path, model_option)` and calls `predict()`.
4. The API returns JSON `{ "emotion": <label>, "probabilities": <map> }`.
