FROM node:16-alpine as builder

WORKDIR /app

COPY package.json .

RUN npm install && npm install react-scripts@3.4.1 -g --silent

COPY . .

RUN npm build

FROM nginx:latest

EXPOSE 3000

COPY default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/shared/nginx/html
