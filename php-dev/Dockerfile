FROM ghcr.io/my-declarative-pc/distroboxes-ubuntu-base

ARG PHP_VERSION="8.3"
RUN nala update && \
    nala install --no-install-recommends -y software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    nala update && \
    nala install --no-install-recommends -y \
        curl \
        nodejs \
        npm \
        php${PHP_VERSION} \
        php${PHP_VERSION}-apcu \
        php${PHP_VERSION}-cli \
        php${PHP_VERSION}-curl \
        php${PHP_VERSION}-gd \
        php${PHP_VERSION}-intl \
        php${PHP_VERSION}-mbstring \
        php${PHP_VERSION}-mysql \
        php${PHP_VERSION}-opcache \
        php${PHP_VERSION}-pgsql \
        php${PHP_VERSION}-soap \
        php${PHP_VERSION}-xdebug \
        php${PHP_VERSION}-xml \
        php${PHP_VERSION}-zip \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/* /var/tmp/*

### Configure PHP
COPY ./configs/php/Z0-main.ini /etc/php/${PHP_VERSION}/cli/conf.d/
COPY ./configs/php/ZZ-apcu.ini /etc/php/${PHP_VERSION}/cli/conf.d/
COPY ./configs/php/ZZ-opcache.ini /etc/php/${PHP_VERSION}/cli/conf.d/
COPY ./configs/php/ZZ-xdebug.ini /etc/php/${PHP_VERSION}/cli/conf.d/
###

### install "Composer"
RUN curl -sS https://getcomposer.org/installer | php${PHP_VERSION} -- --install-dir=/usr/local/bin --filename=composer
###

### install LSP's
RUN npm -g i intelephense \
    @biomejs/biome \
    @fsouza/prettierd \
    prettier \
    typescript \
    typescript-language-server \
    vscode-langservers-extracted && \
    npm cache clean --force
###
