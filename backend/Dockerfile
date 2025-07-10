FROM python:3.12-slim

# Install system dependencies for OpenCV
RUN apt-get update && \
    apt-get install -y \
    libgl1-mesa-glx \
    libgl1-mesa-dri \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender1 \
    libfontconfig1 \
    libxi6 \
    libxrandr2 \
    libpulse0 \
    libdrm2 \
    libgbm1 && \
    ldconfig && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD ["gunicorn", "-b", "0.0.0.0:8080", "app:app"]