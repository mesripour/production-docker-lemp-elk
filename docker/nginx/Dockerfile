FROM nginx:1.16.0

# copy host config file to container
COPY ./docker/nginx/nginx.conf /etc/nginx/nginx.conf

# copy php_listen config file to container
COPY ./docker/nginx/php_listen.conf /etc/nginx/php_listen.conf

# copy index.html to container
COPY ./src/projects/default/index.html /src/default/index.html

# copy host config file to container
COPY ./docker/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf
