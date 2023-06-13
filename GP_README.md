aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com
docker buildx build --platform linux/arm64 -t gp-rtsp-streamer .
docker tag gp-rtsp-streamer:latest 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest
docker push 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest


aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com

docker pull 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest

docker run -it --rm -p 80:8080 277077783554.dkr.ecr.ap-southeast-1.amazonaws.com/gp-rtsp-streamer:latest 
./ngrok http --region=ap --hostname=gpvideo.ap.ngrok.io 80


docker build -t gp-rtsp-streamer-local .

screen
screen -ls 
screen -r [screen id]

TODO need to add the following to the dockerfile
TODO DOCUMENTATION


Need to check 