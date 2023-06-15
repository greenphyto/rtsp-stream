# RTSP Streamer

This repository contains an application for streaming RTSP (Real-Time Streaming Protocol) video. It provides a convenient way to connect to an RTSP server, retrieve the video stream, and display it.

## Deployment

To deploy the application using Docker, follow these steps:

1. Log in to the AWS ECR (Elastic Container Registry) repository:
   ```shell
   aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com
   ```

2. Build the Docker image:
   ```shell
   docker buildx build --platform linux/arm64 -t gp-rtsp-streamer .
   ```

3. Tag the Docker image:
   ```shell
   docker tag gp-rtsp-streamer:latest 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest
   ```

4. Push the Docker image to Amazon ECR:
   ```shell
   docker push 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest
   ```

## Running the Application

To run the application, either locally or on a remote server, follow these steps:

1. Pull the Docker image from Amazon ECR (if running remotely):
   ```shell
   docker pull 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest
   ```

2. Run the Docker container:
   ```shell
   docker run -it --rm -p 80:8080 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest
   ```

3. To expose the application to the internet, you can use ngrok:
   ```shell
   ./ngrok http --region=ap --hostname=gpvideo.ap.ngrok.io 80
   ```

## Local Development

To build and run the application locally, follow these steps:

1. Build the Docker image:
   ```shell
   docker build -t gp-rtsp-streamer-local .
   ```

2. Run the Docker container:
   ```shell
   docker run -it --rm -p 80:8080 gp-rtsp-streamer-local
   ```

## Managing with Screen

To manage the application using the `screen` command, follow these steps:

1. Start a new screen session:
   ```shell
   screen
   ```

2. List all screen sessions:
   ```shell
   screen -ls
   ```

3. Resume a specific screen session:
   ```shell
   screen -r [screen id]
   ```

Feel free to modify the instructions and customize the `readme.md` file to fit your specific use case and project requirements.