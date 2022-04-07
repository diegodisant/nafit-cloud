FROM openresty/openresty:alpine AS builder

WORKDIR /app

FROM builder AS development

COPY . .

COPY docker/nginx/conf.d/nginx.dev.conf /etc/nginx/conf.d/default.conf

FROM development AS production

COPY docker/nginx/conf.d/nginx.prod.conf /etc/nginx/conf.d/default.conf