FROM centos:7.5.1804

# Setup environment
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public

# Update yum
RUN yum update -y

# Add PHP 8.1 repository
RUN yum install epel-release -y
RUN sed -i "s/metalink/#metalink/" /etc/yum.repos.d/epel.repo
RUN sed -i "s/#baseurl=http:\/\/download/baseurl=https:\/\/archives/" /etc/yum.repos.d/epel.repo
RUN yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm yum-utils -y && \
    yum-config-manager --enable remi-php81 && \
    yum update -y

# The zlib1g-dev, libzip-dev, libpng-dev are necessary to enable both `gd` and `zip` extension
# The libicu-dev is necessary to enable `intl` extension
RUN yum install vim wget curl unzip crontabs zlib1g-dev libzip-dev libpng-dev libicu-dev -y

# Install apache
RUN yum install httpd httpd-tools -y

# Installation PHP extensions
RUN yum install php php-json php-gd php-zip php-intl php-mbstring php-pdo php-xml php-mysqlnd -y


# Install Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    rm -rf composer-setup.php

# Copy custom apache configuration into container
COPY httpd.conf /etc/httpd/conf/httpd.conf

# Cleans up the metadata and cache
RUN yum clean all

EXPOSE 80

# Keep container active
# Run apache
ENTRYPOINT ["httpd", "-D", "FOREGROUND"]

