FROM --platform=linux/amd64 python:3.12-slim

WORKDIR /app

RUN apt-get update && apt-get install -y gcc libpq-dev && rm -rf /var/lib/apt/lists/*

COPY ./server/requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt psycopg2

COPY . .

EXPOSE 8000

ENV PYTHONUNBUFFERED=1

WORKDIR /app/server

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]

