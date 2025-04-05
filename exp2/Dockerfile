# Use an official Python runtime as the base image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

# Clone the Streamlit example repository
RUN git clone https://github.com/streamlit/streamlit-example.git .

# Install Python dependencies
RUN pip3 install -r requirements.txt

# Expose port 8501 for Streamlit
EXPOSE 8501

# Health check to ensure the app is running
HEALTHCHECK CMD curl --fail http://localhost:8501/_stcore/health

# Set the entrypoint command to run the Streamlit app
ENTRYPOINT ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
