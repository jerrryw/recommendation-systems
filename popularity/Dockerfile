# Use official slim Python image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Install OS dependencies needed for pip packages
RUN apt-get update && apt-get install -y \
    gcc \
    g++ \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements first to cache dependencies
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy app source code
COPY app/ ./app
COPY .env .env

# Expose FastAPI port
EXPOSE 8000

# Run FastAPI server
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
