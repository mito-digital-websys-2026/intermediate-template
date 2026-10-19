FROM python:3.13-bookworm

WORKDIR /workspace/backend

# mysqlclient のビルドに必要なライブラリ
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    default-libmysqlclient-dev \
    build-essential \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

CMD ["sleep", "infinity"]
