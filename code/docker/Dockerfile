# Pick a matching runtime (example: CUDA 12, Ubuntu 22.04)
FROM nvidia/cuda:12.6.1-cudnn-runtime-ubuntu22.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-venv python3-pip libgomp1 \
 && rm -rf /var/lib/apt/lists/*

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Use the *local* variant to match system CUDA:
RUN pip install --no-cache-dir -U pip \
 && pip install --no-cache-dir -U  "numpy>2" matplotlib "jax[cuda12-local]" jax-cfd[complete] 
 && pip install --no-cache-dir -U  optax
