FROM nginx:1.19-alpine

COPY ./conf /etc/nginx/conf.d
RUN chmod -R 664 /etc/nginx/conf.d

WORKDIR /var/www

EXPOSE 80 443
