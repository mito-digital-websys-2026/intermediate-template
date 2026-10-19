FROM node:22-bookworm

WORKDIR /workspace/frontend

# devcontainer側でbind mountするため、ここではOSパッケージのみ用意する
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    && rm -rf /var/lib/apt/lists/*

CMD ["sleep", "infinity"]
