FROM nginx:1.13-alpine
ENTRYPOINT [ "/docker-entrypoint" ]
CMD [ "nginx", "-g", "daemon off;" ]

ENV BASE_PATH=""

ADD assets/docker-entrypoint /docker-entrypoint
RUN chmod a+x /docker-entrypoint
ADD assets/nginx.conf /etc/nginx/conf.d/default.conf