FROM ubuntu:trusty
MAINTAINER Daniel Hanold (danny@danielhanold.com)

# Environment configuration
# @see https://github.com/docker/docker/issues/4032#issuecomment-192327844
ARG DEBIAN_FRONTEND=noninteractive

# Create user and groups
RUN adduser --home /var/www/localhost/htdocs --disabled-password --gecos "" nginx && \
    addgroup nginx www-data

# Install helper functionality, delete for production mode.
RUN apt-get update && apt-get install -y man vim htop

# Install NGINX
RUN apt-get update && apt-get install -y nginx

# Copy configs
COPY nginx.conf /etc/nginx/nginx.conf
COPY fastcgi_params /etc/nginx/fastcgi_params
COPY drupal.conf /etc/nginx/conf.d/drupal.conf
COPY test.txt /var/www/html/test.txt

# Set the workdirectory.
WORKDIR /var/www/html

# Expose HTTP and HTTPS ports.
EXPOSE 80 443

# Try executing an entrypoint file on launch.
# In entrypoint, run NGINX process in foreground to
# ensure the container doesn't stop after being launched.
# @see http://stackoverflow.com/questions/24241292/dockerized-nginx-is-not-starting
CMD ["nginx", "-g", "daemon off;"]