FROM wajika/alpine-base:latest
MAINTAINER Scott Mebberson <scott@scottmebberson.com>

# Install nginx
RUN echo "http://dl-4.alpinelinux.org/alpine/v3.12/main" >> /etc/apk/repositories && \
    apk add --update nginx=1.18.0 && \
    rm -rf /var/cache/apk/* && \
    chown -R nginx:www-data /var/lib/nginx

# Add the files
ADD root /

# Expose the ports for nginx
EXPOSE 80 443
