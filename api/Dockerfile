# Use NVIDIA's base image with CUDA support (Python 3.9, CUDA 11.7, CUDNN 8)
FROM nvidia/cuda:11.7.1-cudnn8-runtime-ubuntu20.04

# Environment variables to ensure clean execution
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

# Install Python and pip
RUN apt-get update && apt-get install -y python3 python3-pip

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt ./

# Install the dependencies (including PyTorch with CUDA support)
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the app files into the container
COPY . .

EXPOSE 8080

# Command to run the application
CMD ["uvicorn", "api:app", "--host", "0.0.0.0", "--port", "8080", "--log-level", "debug"]