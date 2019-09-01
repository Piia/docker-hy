FROM ubuntu:16.04 

RUN apt-get update && apt-get install -y ffmpeg python python3-pip wget \
    && pip3 install --user --upgrade yle-dl

WORKDIR /app

ENTRYPOINT ["/root/.local/bin/yle-dl"]