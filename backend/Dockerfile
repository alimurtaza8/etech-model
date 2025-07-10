# Use an official Python runtime as a parent image
FROM python:3.12-slim

# Install system dependencies
RUN apt-get update && \
    apt-get install -y libgl1-mesa-glx && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /app

# Copy requirements and install
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your code
COPY . .

# Expose the port (change if your app uses a different port)
EXPOSE 8080

# Command to run your app (adjust if you use a different entrypoint)
CMD ["gunicorn", "-b", "0.0.0.0:8080", "app:app"]