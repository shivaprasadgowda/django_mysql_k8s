# Use official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies required for mysqlclient and other dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    default-libmysqlclient-dev \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Copy the application code into the container
COPY . /app

# Install Python dependencies
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Set environment variables to ensure the app runs in production
ENV PYTHONUNBUFFERED=1

# Expose port 8000 for the application
EXPOSE 8000

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
