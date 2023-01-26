FROM ubuntu:20.04

LABEL maintainer="Ronnie van der Veen <ronnie@vrsoftware.biz>"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && \
	apt-get install -yq tzdata && \
	dpkg-reconfigure -f noninteractive tzdata && \
	apt-get install -yq \
		acl \
		cron \
		curl \
		fontconfig \
		git \
		libxrender1 \
		nginx \
		php-fpm \
		php-gd \
		php-mysql \
		php-xml \
		php-zip \
		php-curl \
		unzip \
		xfonts-75dpi \
		xfonts-base \
		zip && \
    curl -sS https://getcomposer.org/installer | php -- --1 --install-dir=/usr/local/bin --filename=composer && \
	curl -L -o wkhtmltox.deb https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.focal_amd64.deb && \
	dpkg -i wkhtmltox.deb && \
	rm wkhtmltox.deb && \
	apt-get clean && \
	echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 443 80

ENTRYPOINT ["nginx"]
