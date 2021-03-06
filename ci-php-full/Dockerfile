FROM trifs/ci-php-base:5.6.30
MAINTAINER Igor Ajdisek <igor@3fs.si>

# Install Cassandra PHP driver 
RUN sudo apt-get install -y cmake
RUN git clone https://github.com/datastax/php-driver.git && \
    cd php-driver && \
    git reset --hard v1.2.2 && \
    git submodule update --init && \
    cd ext && \
    sudo ./install.sh
RUN echo extension=cassandra.so | sudo tee /etc/php/5.6/cli/conf.d/cassandra.ini

# Ensure cqlsh is available 
RUN curl -O http://archive.apache.org/dist/cassandra/2.0.16/apache-cassandra-2.0.16-bin.tar.gz && \
    tar xf apache-cassandra-2.0.16-bin.tar.gz && \
    sudo mv apache-cassandra-2.0.16/bin/cqlsh /usr/local/bin/ && \
    sudo mv apache-cassandra-2.0.16/pylib /usr/local/ && \
    rm -rf apache-cassandra-2.0.16* && \
    sudo apt-get install -y python-dev python-pip && \
    sudo pip install cql==1.4.0 thrift==0.9.3

# Legacy: compile phlacon support for PHP 
RUN git clone https://github.com/phalcon/cphalcon.git && \
    cd cphalcon && \
    git reset --hard phalcon-v1.3.2 && \
    cd build && \
    sudo ./install
RUN echo extension=phalcon.so | sudo tee /etc/php/5.6/cli/conf.d/phalcon.ini

# Enable php-redis
RUN sudo apt-get install -y php-redis

RUN sudo apt-get install -y zip unzip php5.6-zip php5.6-xml php5.6-soap
