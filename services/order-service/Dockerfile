
FROM python:3.13-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir fastapi httpx "uvicorn>=0.27,<1.0"

COPY app.py common.py ./

RUN mkdir -p /data

ENV PORT=8001
ENV DB_PATH=/data/orders.db
ENV LOG_LEVEL=INFO

ENV INVENTORY_URL=http://inventory-service:8002
ENV PAYMENT_URL=http://payment-service:8003
ENV NOTIFICATION_URL=http://notification-service:8004

EXPOSE 8001

CMD ["sh", "-c", "uvicorn app:app --host 0.0.0.0 --port ${PORT}"]
