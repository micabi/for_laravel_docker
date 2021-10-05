FROM php:8.0-fpm
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

ARG UID=1000
ARG GID=1000
# -m ホームディレクトリ作成 -u ユーザーID
RUN useradd -m -u ${UID} docker

# Nodejs
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
RUN apt-get install -y nodejs
RUN npm i -g npm

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev vim && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath

# ユーザーの切り替え
USER ${UID}:${GID}
