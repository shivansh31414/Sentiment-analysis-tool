# Usage Examples

Using the demo UI

1. Start the frontend: `cd frontend && npm run dev` (port 3000).
2. Start the model API (see `docs/setup.md`) on port 8080.
3. Open `http://localhost:3000/demo` and upload an image.

Direct API example (curl)

```bash
curl -X POST "http://localhost:8080/predict" \
  -F "file=@/path/to/face.jpg" \
  -F "model_option=1"

# Example response:
# { "emotion": "happy", "probabilities": {"happy": 0.88, "neutral": 0.07, ...} }
```

Notes
- The API expects an image file (content-type starting with `image/`).
- `model_option` is an optional form field that is forwarded to the model wrapper.
