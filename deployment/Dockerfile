# Base image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

RUN apt-get update && apt-get install -y curl

# Install UV
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
RUN source $HOME/.local/bin/env (sh, bash, zsh)

# Copy dependency file
COPY uv.lock uv.lock* ./

# Install dependencies with UV
RUN uv install

# Copy app
COPY . .

# Expose Streamlit port
EXPOSE 8501

# Run Streamlit
CMD ["streamlit", "run", "notion_finance.py", "--server.port=8501", "--server.address=0.0.0.0"]

