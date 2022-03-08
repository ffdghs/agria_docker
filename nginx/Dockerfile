FROM nginx:alpine

COPY nginx.conf /etc/nginx/
COPY sites-enabled /etc/nginx/sites-enabled

COPY ssl/nginx-selfsigned.crt /etc/ssl/certs/
COPY ssl/nginx-selfsigned.key /etc/ssl/private/

CMD ["nginx"]

EXPOSE 80
EXPOSE 443