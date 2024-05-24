FROM node:10 AS builder

LABEL maintainer="faly"

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM nginx

COPY nginx/ /etc/nginx/

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh

RUN chmod +x /docker-entrypoint.d/entrypoint.sh

COPY --from=builder /app/dist/*  /usr/share/nginx/html
