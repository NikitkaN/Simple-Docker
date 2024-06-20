FROM ubuntu/nginx
RUN apt-get -y update && apt-get install -y libfcgi-dev && apt-get install -y spawn-fcgi && apt-get install -y nginx && apt-get install -y gcc && apt-get clean && rm -rf /var/lib/apt/lists/*
RUN useradd -d /home/dockle -m -s /bin/bash dockle
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
RUN \
  chmod u-s /bin/umount && \
  chmod g-s /usr/bin/expiry && \
  chmod u-s /bin/su && \
  chmod g-s /usr/bin/wall && \
  chmod u-s /usr/bin/gpasswd && \
  chmod u-s /bin/mount && \
  chmod u-s /usr/bin/passwd && \
  chmod g-s /sbin/unix_chkpwd && \
  chmod g-s /usr/bin/chage && \
  chmod u-s /usr/bin/chsh && \
  chmod u-s /usr/bin/chfn && \
  chmod u-s /usr/bin/newgrp && \
  chmod g-s /usr/sbin/pam_extrausers_chkpwd
USER dockle
WORKDIR serv
COPY ./server.c server.c
COPY ./start.sh start.sh
CMD [ "./start.sh" ]
