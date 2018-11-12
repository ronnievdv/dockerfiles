FROM ubuntu:18.04

LABEL maintainer="Ronnie van der Veen <ronnie@vrsoftware.biz>"

ENV TZ 'UCT'

RUN echo $TZ > /etc/timezone && \
	echo "deb http://security.ubuntu.com/ubuntu xenial-security main" >> /etc/apt/sources.list && \
	apt-get update && apt-get install -yq tzdata && \
	rm /etc/localtime && \
	ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
	dpkg-reconfigure -f noninteractive tzdata && \
    apt-get install -yq \
		acl \
		cron \
		curl \
		fontconfig \
		git \
		libpng12-0 \
		libxrender1 \
		nginx \
		php-fpm \
		php-gd \
		php-mysql \
		php-xml \
		php-zip \
		unzip \
		xfonts-75dpi \
		xfonts-base \
		zip && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
	curl -L -o wkhtmltox.deb https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.xenial_amd64.deb && \
	dpkg -i wkhtmltox.deb && \
	rm wkhtmltox.deb && \
	apt-get clean && \
	echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 443 80

ENTRYPOINT ["nginx"]
