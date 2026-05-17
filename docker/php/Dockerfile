# FROM php:8.5-fpm-alpine
FROM public.ecr.aws/docker/library/php:8.5-fpm-alpine
COPY ./docker/php/php.ini /usr/local/etc/php/conf.d/90-php.ini
COPY ./backend /var/www/html