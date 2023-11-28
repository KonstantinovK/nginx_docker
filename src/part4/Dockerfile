FROM nginx

WORKDIR /home/
COPY ./fastcgi_server.c .
COPY ./start_server.sh .
COPY ./nginx.conf /etc/nginx/nginx.conf
RUN apt-get update && apt-get install -y gcc spawn-fcgi libfcgi-dev

ENTRYPOINT ["bash", "./start_server.sh"]
