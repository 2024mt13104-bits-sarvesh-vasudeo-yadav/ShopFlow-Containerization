
FROM python:3.13-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir fastapi "uvicorn[standard]"

COPY app.py common.py ./

RUN mkdir -p /data

ENV PORT=8004
ENV DB_PATH=/data/notification.db
ENV LOG_LEVEL=INFO
ENV NOTIFICATION_FAIL=false
ENV NOTIFICATION_DELAY_SECONDS=0

EXPOSE 8004

CMD ["sh", "-c", "uvicorn app:app --host 0.0.0.0 --port ${PORT}"]
