FROM trifs/ci-puppet
MAINTAINER Igor Ajdisek <igor@3fs.si>

RUN export LANG=C.UTF-8 && sudo apt-add-repository -y ppa:ondrej/php && \
    sudo apt-add-repository -y ppa:linuxjedi/ppa   && \
    sudo apt-get update -qq                        && \
    sudo apt-get install -y libuv-dev libgmp-dev   && \
    sudo apt-get install -y openssl libssl-dev     && \
    sudo apt-get install -y php5.6-intl php5.6-cli php5.6-dev php5.6-curl php5.6-common

# Enable Xdebug and Imagick extensions
RUN sudo apt-get install -y php5.6-xdebug php5.6-imagick
