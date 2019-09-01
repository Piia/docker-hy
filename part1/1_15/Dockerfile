FROM gradle
COPY SocketChat .
RUN gradle bigJar
ENTRYPOINT java -jar build/libs/SocketChat-all.jar