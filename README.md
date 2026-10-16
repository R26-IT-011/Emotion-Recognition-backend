# Faceo Analytics — Emotion Recognition Microservice (SSD MobileNetV3)

FastAPI microservice for facial emotion detection running on Port 8002.
Part of the FACEO Facial Intelligence Platform.

## Features
- **Model**: MobileNetV3 PyTorch architecture
- **Emotions**: Angry, Disgust, Fear, Happy, Sad, Surprise, Neutral
- **Container**: Production-ready Dockerfile optimized for Google Cloud Run (CPU-only PyTorch)
- **Port**: Supports dynamic `$PORT` environment variable (defaults to 8002)

## Local Run
```bash
pip install -r requirements.txt
python main.py
```

## Docker Build & Run
```bash
docker build -t faceo-emotion-service .
docker run -p 8002:8002 -e PORT=8002 faceo-emotion-service
```

## GCP Cloud Run Deployment
```bash
gcloud run deploy faceo-emotion-service \
  --source . \
  --region asia-southeast1 \
  --min-instances 0 \
  --max-instances 1 \
  --memory 1Gi \
  --cpu 1 \
  --cpu-throttling \
  --allow-unauthenticated
```
