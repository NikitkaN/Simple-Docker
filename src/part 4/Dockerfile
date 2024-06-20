FROM nginx:latest
WORKDIR /etc/nginx
ARG USERNAME=nginx
COPY ../server/server.c .
COPY ./start.sh .
RUN apt-get update && apt-get -y install && \
  apt-get install gcc -y && \
  apt-get install spawn-fcgi -y && \
  gcc -o ./server.fcgi ./server.c -lpthread -lfcgi && \
  rm -rf /var/lib/apt/lists
COPY ../server/server.c .
COPY ../nginx/nginx.conf
USER $USERNAME
CMD ["./start.sh"]
