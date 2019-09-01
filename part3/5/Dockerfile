FROM node as build
WORKDIR /1_10
COPY ../../part1/1_10/frontend-example-docker .

RUN npm install && npm build

FROM node
WORKDIR /1_10
COPY --from=build /dist /dist

RUN npm install -g serve && useradd -m app

USER app
EXPOSE 5000
ENV API_URL=http://localhost:8000

ENTRYPOINT serve -s -l 5000 dist