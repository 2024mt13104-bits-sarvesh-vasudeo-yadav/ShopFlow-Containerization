
FROM python:3.13-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir fastapi "uvicorn[standard]"

COPY app.py common.py ./

RUN mkdir -p /data

ENV PORT=8003
ENV DB_PATH=/data/payment.db
ENV LOG_LEVEL=INFO

EXPOSE 8003

CMD ["sh", "-c", "uvicorn app:app --host 0.0.0.0 --port ${PORT}"]
