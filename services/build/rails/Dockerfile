FROM ruby:3.2.2-alpine

ENV BUNDLER_VERSION=2.5.4

RUN apk add --update --no-cache \
  binutils-gold \
  build-base \
  curl \
  file \
  g++ \
  gcc \
  git \
  less \
  libstdc++ \
  libffi-dev \
  libc-dev \ 
  linux-headers \
  libxml2-dev \
  libxslt-dev \
  libgcrypt-dev \
  make \
  netcat-openbsd \
  openssl \
  pkgconfig \
  postgresql-dev \
  python3 \
  tzdata

RUN gem install bundler -v 2.5.4

WORKDIR /app

COPY Gemfile Gemfile.lock ./

RUN bundle config build.nokogiri --use-system-libraries

RUN bundle check || bundle install 

COPY . ./ 

ENTRYPOINT ["./services/entrypoints/docker-entrypoint.sh"]
