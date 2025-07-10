# Use a stable Python version that is well-supported
FROM python:3.11-slim

# The critical step: Set the environment variable to tell the OS where to find shared libraries.
# This is the definitive fix for the "cannot open shared object file" error.
ENV LD_LIBRARY_PATH /usr/lib/x86_64-linux-gnu/

# Install a comprehensive set of system dependencies required by OpenCV and Ultralytics.
RUN apt-get update && apt-get install -y --no-install-recommends \
    libgl1-mesa-glx \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /app

# Copy and install Python requirements
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your application code into the container
COPY . .

# Set the command to run your application with Gunicorn
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:$PORT"] 