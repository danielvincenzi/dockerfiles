FROM alpine:3.8

LABEL maintainer "Daniel Vincenzi <danielvincenzi@icloud.com>"

# Environments
ENV VERSION "1.9.0"
ENV TZ "America/Sao_Paulo"

RUN \ 
    # Install dependencies
    apk --update --no-cache add \
      autoconf \
      autoconf-doc \
      automake \
      c-ares \
      c-ares-dev \
      curl \
      gcc \
      libc-dev \
      libevent \
      libevent-dev \
      libtool \
      make \
      man \
      libressl-dev \
      pkgconfig \
      postgresql-client \
      tzdata && \
    # Unpack and compile
    curl --output /tmp/pgbouncer-$VERSION.tar.gz -L https://pgbouncer.github.io/downloads/files/$VERSION/pgbouncer-$VERSION.tar.gz && \
    cd /tmp && \
    tar xvzf /tmp/pgbouncer-$VERSION.tar.gz && \
    cd pgbouncer-$VERSION && \
    ./configure --prefix=/usr && \
    make && \
    # Manual install
    cp pgbouncer /usr/bin && \
    mkdir -p /etc/pgbouncer /var/log/pgbouncer /var/run/pgbouncer && \
    chown -R nobody:nogroup /var/run/pgbouncer /var/log/pgbouncer && \
    # Context cleanup 
    rm -rf /tmp/* && \
    apk --purge del \
      autoconf \
      autoconf-doc \
      automake \
      c-ares-dev \
      curl \
      gcc \
      libc-dev \
      libevent-dev \
      libtool \
      make \
      man \
      libressl-dev \
      pkgconfig

# Copy files
COPY pgbouncer.ini /etc/pgbouncer
COPY userlist.txt /etc/pgbouncer

# Select user
USER nobody 

# Set volumes
VOLUME ["/etc/pgbouncer", "/etc/ssl"]

# Port expose
EXPOSE 6432

# Initial command
CMD ["pgbouncer", "/etc/pgbouncer/pgbouncer.ini"]
