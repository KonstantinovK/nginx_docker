FROM nginx

WORKDIR /home/

COPY ./fastcgi_server.c .
COPY ./start_server.sh .
COPY ./nginx.conf /etc/nginx/nginx.conf

RUN apt update && apt install -y gcc spawn-fcgi libfcgi-dev ; \
    apt clean && rm -rf /var/lib/apt/lists/*; \
    useradd mini_serv; \
    chown -R mini_serv:mini_serv /etc/nginx/nginx.conf; \
    chown -R mini_serv:mini_serv /var/cache/nginx; \
    chown -R mini_serv:mini_serv /home/; \
    touch /var/run/nginx.pid && chown -R mini_serv:mini_serv /var/run/nginx.pid; \
    chmod u-s /usr/bin/gpasswd; \
    chmod u-s /usr/bin/chsh; \
    chmod u-s /usr/bin/chfn; \
    chmod g-s /usr/bin/expiry; \
    chmod u-s /usr/bin/passwd; \
    chmod g-s /sbin/unix_chkpwd; \
    chmod g-s /usr/bin/chage; \
    chmod g-s /usr/bin/wall; \
    chmod u-s /bin/umount; \
    chmod u-s /bin/mount; \
    chmod u-s /usr/bin/newgrp; \
    chmod u-s /bin/su; \
    chmod u-s /usr/bin/chsh;

USER mini_serv

HEALTHCHECK CMD curl http://localhost:81/ || exit 1

ENTRYPOINT ["bash", "./start_server.sh"]
