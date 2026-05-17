# FROM nginx:1.30.0-alpine
FROM public.ecr.aws/docker/library/nginx:1.30.0-alpine
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf
COPY ./backend /usr/share/nginx/html