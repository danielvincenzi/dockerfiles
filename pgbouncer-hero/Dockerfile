FROM ruby:2.5-alpine3.7

MAINTAINER "Daniel Vincenzi <danielvincenzi@icloud.com>"

# Environments
ENV RAILS_ENV "development"
ENV RAILS_SERVE_STATIC_FILES "true"
ENV PGBOUNCERHERO_DATABASE_URL "postgres://stats:stats@pgbouncer:6432/pgbouncer"
ENV TZ "America/Sao_Paulo"

# Select directory
WORKDIR /usr/src/app

# Copy files
COPY . .

RUN \
    # Install dependencies
    apk --update --no-cache add \
      curl-dev \
      ruby-dev \
      build-base \
      zlib-dev \
      libxml2-dev \
      libxslt-dev \
      yaml-dev \
      sqlite-dev \
      postgresql-dev \
      ruby \
      ruby-io-console \
      ruby-json \
      yaml \
      nodejs \
      tzdata && \
    # Install Gems
    gem install -N bundler && \
    gem install -N nokogiri -- --use-system-libraries && \
    gem install -N rails --version 4.2.10 && \
    # Settings
    bundle config --global build.nokogiri  "--use-system-libraries" && \
    bundle config --global build.nokogumbo "--use-system-libraries" && \
    # Bundle launch
    bundle install && \
    bundle exec rake assets:precompile

# Port expose
EXPOSE 8080

# Initial command
CMD ["rails", "server", "-b", "0.0.0.0", "--port", "8080"]
