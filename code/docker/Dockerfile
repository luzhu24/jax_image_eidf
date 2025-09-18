FROM python:3.11-slim

RUN apt-get update && apt-get install -y --no-install-recommends libgomp1 && \
    rm -rf /var/lib/apt/lists/*

ENV VIRTUAL_ENV=/opt/venv
RUN python -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install JAX with bundled CUDA/cuDNN, plus your deps
RUN pip install -U pip && \
    pip install -U "jax[cuda12]" jax-cfd[completed] optax matplotlib numpy seaborn

# Optional: sanity check
# RUN python - <<'PY'\nimport jax; print(jax.devices())\nPY
