# Use the official Python 3.9 image as a base for building
FROM python:3.9.6 AS builder

# Environment variables to ensure clean execution
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

# Set the working directory inside the container
WORKDIR /app

# Create a virtual environment
RUN python -m venv .venv

# Copy the requirements file into the container
COPY requirements.txt ./

# Install the dependencies inside the virtual environment
RUN .venv/bin/pip install -r requirements.txt

# Slim version of Python as the runtime environment
FROM python:3.9.6-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the virtual environment from the builder stage
COPY --from=builder /app/.venv .venv/

# Copy the rest of the app files into the container
COPY . .

# Command to run the app using the virtual environment and your main.py
CMD ["/app/.venv/bin/python", "main.py"]