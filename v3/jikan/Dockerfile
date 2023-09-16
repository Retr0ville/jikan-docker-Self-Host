FROM	php:7.4-apache-buster
ENV	COMPOSER_ALLOW_SUPERUSER	1
RUN	apt-get update && apt-get install -y \
	openssl \
	git \
	unzip \
	&& curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
	&& composer --version
RUN	git clone --branch=v3 --depth=1 https://github.com/Retr0ville/Jikan-at-v3-SelfHost.git . \
	&& composer require 'composer/package-versions-deprecated' \
	&& composer install --prefer-dist --no-progress --classmap-authoritative  --no-interaction \
	&& composer update Jikan-at-v3-SelfHost/jikan
ADD	.env	/run-jikan.sh	./
ENTRYPOINT	["./run-jikan.sh"]
