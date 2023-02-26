FROM php:7.4-fpm-alpine

RUN apk --no-cache add pcre-dev ${PHPIZE_DEPS} \ 
  && pecl install xdebug-3.1.4 \
  && docker-php-ext-enable xdebug \
  && apk del pcre-dev ${PHPIZE_DEPS}
  
RUN docker-php-ext-install opcache 
# COPY php/production/opcache.ini /usr/local/etc/php/conf.d/opcache.ini
