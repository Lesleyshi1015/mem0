FROM --platform=linux/amd64 python:3.12-slim

WORKDIR /app

COPY ./server/requirements.txt .


RUN pip install psycopg2-binary

RUN pip install --no-cache-dir -r ./server/requirements.txt


COPY . .

EXPOSE 8000

ENV PYTHONUNBUFFERED=1

WORKDIR /app/server

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]

