FROM wajika/alpine-base:latest
MAINTAINER Scott Mebberson <scott@scottmebberson.com>

# Install apache
RUN apk add --no-cache apache2=2.4.43-r0 apache2-utils=2.4.43-r0

RUN mkdir -p /run/apache2/

# Add the files
ADD root /

# Expose the ports for apache
EXPOSE 80 443
