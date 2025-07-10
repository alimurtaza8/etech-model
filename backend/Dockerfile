FROM python:3.12-slim

# Install system dependencies for OpenCV
RUN apt-get update && \
    apt-get install -y \
    libgl1-mesa-glx \
    libgl1-mesa-dri \
    libgl1-mesa-dev \
    libxrender1 \
    libxext6 \
    libx11-6 \
    libxtst6 \
    libxi6 \
    libglib2.0-0 \
    libsm6 && \
    ldconfig && \
    rm -rf /var/lib/apt/lists/*

# Set LD_LIBRARY_PATH to ensure the libraries are found
ENV LD_LIBRARY_PATH /usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD ["gunicorn", "-b", "0.0.0.0:8080", "app:app"]