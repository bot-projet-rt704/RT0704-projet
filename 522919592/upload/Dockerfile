FROM python:3-alpine3.7

COPY boot.sh /
RUN chmod +x /boot.sh

RUN apk add -q --update --no-cache \
        tini \
        git \
        openssh-client \
        build-base \
        openssh-client \
        autoconf \
        automake \
        libtool \
        zlib-dev \
        curl-dev \
        libffi-dev \
        openssl-dev \
    && echo 'StrictHostKeyChecking no' >> /etc/ssh/ssh_config \
    && git clone https://github.com/maxmind/geoipupdate \
    && cd geoipupdate \
    && ./bootstrap \
    && ./configure \
    && make \
    && make install \
    && cd .. \
    && rm -rf ./geoipupdate \
    && rm -rf /var/cache/apk/*

RUN mkdir /app
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt

ENV PORT 8000
EXPOSE $PORT

ENV APP_MODULE app:app
ENV TIMEOUT 60
ENV WORKERS 4
ENV ACCESSLOG -
ENV ERRORLOG -
ENV PIDFILE app.pid

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["/boot.sh"]

