FROM node:18-alpine

COPY . /app

WORKDIR /app

RUN npm i -g @nestjs/cli ts-node
RUN npm install

RUN npm run build

EXPOSE 3001
