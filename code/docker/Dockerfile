FROM python:3.11-slim

RUN apt-get update && apt-get install -y --no-install-recommends libgomp1 && \
    rm -rf /var/lib/apt/lists/*

# Isolate Python
ENV VIRTUAL_ENV=/opt/venv
RUN python -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Friendlier GPU memory behavior when TF & JAX coexist (change if you prefer)
ENV TF_FORCE_GPU_ALLOW_GROWTH=true \
    XLA_PYTHON_CLIENT_PREALLOCATE=false

# Install JAX with bundled CUDA/cuDNN, plus your deps
RUN pip install -U pip && \
    pip install -U "tensorflow[and-cuda]" "jax[cuda12]" jax-cfd[complete] optax matplotlib numpy seaborn

# Optional: sanity check
# RUN python - <<'PY'\nimport jax; print(jax.devices())\nPY
