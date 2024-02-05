FROM httpd:2.4-alpine

# Set up environment
ENV APP_ROOT=/var/www
ENV SERVER_NAME=localhost
ENV DOCUMENT_ROOT=${APP_ROOT}/public
ENV APACHE_LOG_DIR=${APP_ROOT}/docker/apache/logs
ENV APACHE_RUN_GROUP=www-data
ENV APACHE_RUN_USER=www-data

# Working folder
WORKDIR ${APP_ROOT}

RUN mkdir -p ${DOCUMENT_ROOT}
RUN chown -R ${APACHE_RUN_USER}:${APACHE_RUN_USER} ${DOCUMENT_ROOT}

# Create a symbolic link to index.php
RUN ln -s ${APP_ROOT}/public/index.php ${DOCUMENT_ROOT}

# Copy custom Apache configuration
COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
