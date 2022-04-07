FROM php:8.0-fpm-alpine AS builder

WORKDIR /app

RUN docker-php-ext-install \
    pdo \
    pdo_qsql && \
    docker-php-ext-enable pdo \
    pdo_qsql

FROM builder AS development

COPY . .

COPY docker/php/php.dev.ini ${PHP_INI_DIR}/conf.d/php.ini

FROM development AS production

COPY --from=development /app /app
COPY docker/php/php.prod.ini ${PDO_INI_DIR}/conf.d/php.ini