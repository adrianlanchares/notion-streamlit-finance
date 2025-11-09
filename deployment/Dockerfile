# Base image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

# Install UV
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Copy dependency file
COPY uv.yaml uv.lock* ./  # include uv.lock if you have one

# Install dependencies with UV
RUN uv install

# Copy app
COPY . .

# Expose Streamlit port
EXPOSE 8501

# Run Streamlit
CMD ["streamlit", "run", "notion_finance.py", "--server.port=8501", "--server.address=0.0.0.0"]

