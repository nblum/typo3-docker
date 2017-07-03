FROM debian:8.7

RUN apt-get update && \
    apt-get install -y apt-transport-https lsb-release ca-certificates wget && \
    wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list && \
    apt-get update && \
    apt-get install -y \
      nano \
      apache2 \
      php7.1 \
      php7.1-cli \
      libapache2-mod-php7.1 \
      php7.1-gd \
      php7.1-json \
      php7.1-ldap \
      php7.1-mbstring \
      php7.1-mysql \
      php7.1-pgsql \
      php7.1-sqlite3 \
      php7.1-xml \
      php7.1-xsl \
      php7.1-zip \
      php7.1-soap && \
      apt-get upgrade -yfq && apt-get autoremove -y && apt-get clean && rm -rf /var/lib/apt/lists/*
      
#Apache config
RUN mkdir -p /var/www/html/web/
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

#Bootstrap
COPY entrypoint.sh /usr/local/bin/entrypoint
WORKDIR /var/www/html
ENTRYPOINT ["entrypoint"]
