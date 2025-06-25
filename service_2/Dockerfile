FROM python:3.12-slim-bookworm

# Install curl and certs to fetch uv
RUN apt-get update && apt-get install -y --no-install-recommends curl ca-certificates

# Download and install uv
ADD https://astral.sh/uv/install.sh /uv-installer.sh
RUN sh /uv-installer.sh && rm /uv-installer.sh

# Ensure uv is on PATH
ENV PATH="/root/.local/bin/:$PATH"

# Set working directory
WORKDIR /app

# Copy only dependency files
COPY pyproject.toml uv.lock ./

# Create virtual env and install dependencies using uv
RUN uv venv && \
    .venv/bin/python -m ensurepip --upgrade && \
    uv sync

# Copy app source code
COPY . .

# Expose the port your app runs on
EXPOSE 8002

# Run app using uv’s virtual environment
CMD [".venv/bin/python", "app.py"]
