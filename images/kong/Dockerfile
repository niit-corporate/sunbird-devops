#FROM kong:0.9.9

# ensure Kong logs go to the log pipe from our entrypoint and so to docker logging
#RUN mkdir -p /usr/local/kong/logs \
#    && ln -sf /dev/stdout /usr/local/kong/logs/serf.log \
#    && ln -sf /dev/stderr /usr/local/kong/logs/error.log \
#    && ln -sf /dev/stdout /usr/local/kong/logs/access.log


#=========================================================================


FROM centos:7

ENV KONG_VERSION 0.10.3

RUN yum install -y wget https://github.com/Mashape/kong/releases/download/$KONG_VERSION/kong-$KONG_VERSION.el7.noarch.rpm && \
    yum clean all

RUN wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.1.3/dumb-init_1.1.3_amd64 && \
    chmod +x /usr/local/bin/dumb-init

RUN yum install -y net-tools

COPY docker-entrypoint.sh /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]

# ensure Kong logs go to the log pipe from our entrypoint and so to docker logging
RUN mkdir -p /usr/local/kong/logs \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/access.log \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/serf.log \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/error.log
ENV HTTP_PROXY "http://172.23.32.211:8080"
ENV HTTPS_PROXY "http://172.23.32.211:8080"
ENV NO_PROXY "localhost,sunbird-idc.niiteducation.com,172.23.32.204,172.23.32.139,172.23.32.148,172.23.32.234,172.23.32.149,172.23.32.145,172.23.32.146,172.23.32.147,172.23.32.143,172.23.32.144,github.com"
ENV http_proxy "http://172.23.32.211:8080"
ENV https_proxy "http://172.23.32.211:8080"
ENV no_proxy "localhost,sunbird-idc.niiteducation.com,172.23.32.204,172.23.32.139,172.23.32.148,172.23.32.234,172.23.32.149,172.23.32.145,172.23.32.146,172.23.32.147,172.23.32.143,172.23.32.144,github.com"


EXPOSE 8000 8443 8001 7946
CMD ["kong", "start"]
