FROM node
EXPOSE 5000
ENV API_URL=http://localhost:8000
WORKDIR /1_10
COPY . .
RUN npm install
ENTRYPOINT npm start