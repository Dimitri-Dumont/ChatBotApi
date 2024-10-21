# Use the official Python 3.9 image as a base for building
FROM python:3.9-slim

# Environment variables to ensure clean execution
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt ./

# Install the dependencies inside the virtual environment
RUN pip install --no-cache-dir -r requirements.txt


# Set the working directory inside the container
WORKDIR /app

# Copy the rest of the app files into the container
COPY . .

CMD ["uvicorn", "api:app", "--host", "0.0.0.0", "--port", "8000"]