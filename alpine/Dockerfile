FROM python:2.7.12-alpine

RUN apk add --no-cache \
        build-base bash git linux-headers \
        libuv libuv-dev \
        openssl openssl-dev \
        lua5.1 lua5.1-dev

RUN git clone https://github.com/aerospike/aerospike-client-c && \
    cd aerospike-client-c && \
    git checkout tags/4.1.6 && \
    git submodule update --init && \
    make

# ENV AEROSPIKE_C_HOME=/aerospike-client-c
ENV DOWNLOAD_C_CLIENT=0 \
    PREFIX=/aerospike-client-c/target/Linux-x86_64 \
    AEROSPIKE_LUA_PATH=/aerospike-client-c/modules/lua-core/src

RUN pip install aerospike==2.1.1
