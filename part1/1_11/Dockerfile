FROM node
EXPOSE 8000
ENV FRONT_URL=http://localhost:5000
WORKDIR /1_11
COPY . .
RUN npm install
ENTRYPOINT npm start