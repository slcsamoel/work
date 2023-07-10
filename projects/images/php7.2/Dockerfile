FROM ubuntu:18.04

ARG USER_ID
ARG GROUP_ID

RUN apt-get update && \
    apt-get install -y tzdata && \
    echo date && \
    apt-get install -y sudo && \ 
    sudo apt-get install -y curl 

RUN apt-get update && \
    sudo apt install -y software-properties-common && \
    sudo add-apt-repository ppa:ondrej/php && \
    sudo apt install -y php7.2 && \
    sudo apt-get install -y composer

RUN sudo apt-get install -y  \
    php7.2-mbstring \
    php7.2-xml \
    php7.2-bcmath \
    php7.2-common \
    openssl \
    php7.2-json \
    php7.2-zip \
    php7.2-curl \
    php-imagick

RUN addgroup --gid $GROUP_ID user
RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID user
USER user