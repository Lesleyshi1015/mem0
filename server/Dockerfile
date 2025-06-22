# ===================================================================
#  这是【唯一正确的最终版 Dockerfile】，请完整复制
# ===================================================================

# 【最关键的修正】: 我们不再从任何公共地址获取基础镜像。
# 我们直接从你自己的腾讯云仓库里，获取我们刚刚用“骗术”得到的那个 python 镜像！
FROM --platform=linux/amd64 ccr.ccs.tencentyun.com/digital-enterprise/python:3.12-slim

# 后面的步骤保持不变，它们是正确的
WORKDIR /app
RUN apt-get update && apt-get install -y gcc libpq-dev && rm -rf /var/lib/apt/lists/*
COPY ./server/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt psycopg2
COPY . .
EXPOSE 8000
ENV PYTHONUNBUFFERED=1
WORKDIR /app/server
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
