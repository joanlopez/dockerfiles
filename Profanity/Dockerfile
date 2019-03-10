FROM debian:stretch

ARG LIBSTROPHE_VERSION=0.9.2
ARG PROFANITY_VERSION=0.6.0

# Installing dependencies
RUN apt-get update \
    && apt-get -y install build-essential libxml2 libxml2-dev libssl-dev pkg-config \
       libtool autoconf wget libncursesw5-dev libglib2.0-dev libcurl3-dev libreadline-dev

# Installing libstrophe (https://github.com/strophe/libstrophe)
RUN cd /tmp \
    && wget https://github.com/strophe/libstrophe/releases/download/${LIBSTROPHE_VERSION}/libstrophe-${LIBSTROPHE_VERSION}.tar.gz \
    && tar xzvf libstrophe-${LIBSTROPHE_VERSION}.tar.gz \
    && cd libstrophe-${LIBSTROPHE_VERSION} \
    && ./bootstrap.sh \
    && ./configure --prefix=/usr \
    && make && make install

# Installing Profanity (http://www.profanity.im)
RUN cd /tmp \
    && wget http://www.profanity.im/profanity-${PROFANITY_VERSION}.tar.gz \
    && tar xzvf profanity-${PROFANITY_VERSION}.tar.gz \
    && cd profanity-${PROFANITY_VERSION} \
    && ./configure \
    && make && make install

RUN rm -rf /tmp/*

CMD ["profanity"]
