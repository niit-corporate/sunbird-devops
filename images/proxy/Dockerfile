FROM nginx:1.13.8-alpine

ENV HTTP_PROXY "http://172.23.32.211:8080"
ENV HTTPS_PROXY "http://172.23.32.211:8080"
ENV NO_PROXY "localhost,sunbird-idc.niiteducation.com,172.23.32.204,172.23.32.139,172.23.32.148,172.23.32.234,172.23.32.149,172.23.32.145,172.23.32.146,172.23.32.147,172.23.32.143,172.23.32.144,github.com"
ENV http_proxy "http://172.23.32.211:8080"
ENV https_proxy "http://172.23.32.211:8080"
ENV no_proxy "localhost,sunbird-idc.niiteducation.com,172.23.32.204,172.23.32.139,172.23.32.148,172.23.32.234,172.23.32.149,172.23.32.145,172.23.32.146,172.23.32.147,172.23.32.143,172.23.32.144,github.com"

RUN rm -rf /etc/nginx/conf.d

RUN rm -rf /usr/share/nginx/html
