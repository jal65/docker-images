FROM mogtofu33/alpine-base:edge

MAINTAINER moimog33@gmail.com

# Set specific uid/gid to web server user to fix permissions issues.
#ENV LOCAL_UID= \
#    LOCAL_GID=

# Variables
ENV MYSQL_DATABASE=drupal \
    MYSQL_USER=drupal \
    MYSQL_PASSWORD=drupal \
    MYSQL_ROOT_PASSWORD=root

RUN apk --update add mysql mysql-client pwgen && \
    rm -rf /var/cache/apk/*

# Copy mysql conf
COPY config/my.cnf /etc/mysql/my.cnf

# Copy startup script
COPY scripts/run.sh /scripts/run.sh
RUN chmod +x /scripts/run.sh

EXPOSE 3306

VOLUME ["/var/lib/mysql", "/var/log/mysql"]

ENTRYPOINT ["/bin/bash" , "/scripts/run.sh"]
