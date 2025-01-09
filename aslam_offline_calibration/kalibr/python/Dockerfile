# Use the official Python 3.10.12 image from Docker Hub
FROM python:3.10.12-slim

# Create user
ARG USER_ID=1000
ARG GROUP_ID=1000
ARG USER_NAME=fiducial

RUN groupadd -g $GROUP_ID $USER_NAME && \
    useradd -m -u $USER_ID -g $GROUP_ID $USER_NAME

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install system pacakges
RUN apt-get update && apt-get install -y \
  texlive-base 

# Install the pip requirements
RUN pip install --no-cache-dir -r requirements.txt

# Set the default user
USER $USER_NAME

# Specify the command to run on container start
ENTRYPOINT ["python", "kalibr_create_target_pdf"]
