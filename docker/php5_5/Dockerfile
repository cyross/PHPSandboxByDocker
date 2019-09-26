# CentOS7にPHP5.5とComposerを入れるDockerfile

# imageはcentos:7
FROM centos:7

# ビルドに必要なCentOSのパッケージとApache、PHPをインストール
RUN yum -y update

RUN yum -y install httpd
RUN systemctl enable httpd.service

RUN yum -y install epel-release
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum install -y --enablerepo=epel gcc-c++ autoconf automake openssl-devel libmcrypt libxml2-devel libxslt-devel zlib zlib-devel libjpeg libpng-devel freetype freetype-devel libedit-devel libtool libtiff libtiff-devel libX11-devel libXpm libXpm-devel fontconfig-devel libtool-ltdl t1lib
RUN yum install -y --disablerepo=base --enablerepo=epel,remi,remi-safe,remi-php55 php php-devel php-mbstring php-pdo php-gd php-xml php-mcrypt php-pecl-zip
RUN yum clean all

# Composerをインストール
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# Laravelをインストール
RUN composer global require laravel/installer
