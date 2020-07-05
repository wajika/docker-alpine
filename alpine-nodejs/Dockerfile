FROM wajika/alpine-base:latest
MAINTAINER Scott Mebberson <scott@scottmebberson.com>

ENV NODE_VERSION=v9.8.0 NPM_VERSION=6

RUN addgroup node && \
    adduser -D -g "" -s /bin/sh -G node node && \
    apk upgrade --update && \
    apk add --update git curl make gcc g++ python2 linux-headers libgcc libstdc++ && \
    curl -sSL https://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}.tar.gz | tar -xz && \
    cd /node-${NODE_VERSION}
RUN echo '====================================================='
RUN grep -c ^processor /proc/cpuinfo
RUN echo '====================================================='
RUN echo ${NODE_VERSION}
WORKDIR /node-${NODE_VERSION}
RUN pwd
RUN ls -lh
RUN ./configure --prefix=/usr --without-snapshot
    #make -j$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
RUN make -j32 && \
    make install
RUN cd / && \
    npm install -g npm@${NPM_VERSION}
RUN apk del gcc g++ linux-headers && \
    rm -rf /etc/ssl /node-${NODE_VERSION} /usr/include \
    /usr/share/man /tmp/* /var/cache/apk/* /root/.npm /root/.node-gyp \
    /usr/lib/node_modules/npm/man /usr/lib/node_modules/npm/doc /usr/lib/node_modules/npm/html

# Add the files
COPY root /
