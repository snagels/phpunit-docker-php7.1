# PHPUnit 6.0.6 Docker Container
FROM ubuntu:16.04
MAINTAINER Sebastian Nagels <nagels.sebastian@gmail.com>

WORKDIR /tmp

RUN apt-get update && apt-get install -y software-properties-common

RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php

RUN apt-get update && apt-get install -y \
		git \
		curl \
		php7.1 \
		php7.1-dom \
		php7.1-bcmath \
		php7.1-zip \
		php7.1-mongodb \
		php7.1-bz2 \
		php7.1-curl \
		php7.1-mbstring \
		php7.1-mysqli \
		php7.1-sqlite \
		php7.1-xdebug \
	&& php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
	&& php composer-setup.php --install-dir=/usr/bin --filename=composer \
	&& composer require "phpunit/phpunit:~6.0.6" --prefer-source --no-interaction \
	&& composer require "phpunit/php-invoker" --prefer-source --no-interaction \
	&& ln -s /tmp/vendor/bin/phpunit /usr/local/bin/phpunit \
	&& php -m | grep -i xdebug

VOLUME ["/app"]
WORKDIR /app

ENTRYPOINT ["/usr/local/bin/phpunit"]
CMD ["--help"]
