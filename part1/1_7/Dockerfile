FROM ubuntu:16.04
WORKDIR /1_7
RUN apt-get update && apt-get install -y curl
COPY myscript.sh .
CMD ["sh", "./myscript.sh"]