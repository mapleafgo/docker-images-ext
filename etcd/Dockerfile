FROM alpine

ARG ETCD_VER=v3.5.4
ARG DOWNLOAD_URL=https://mirrors.huaweicloud.com/etcd

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.huaweicloud.com/g' /etc/apk/repositories && apk add --no-cache tzdata &&\
    wget -q -O /tmp/etcd-${ETCD_VER}-linux-amd64.tar.gz ${DOWNLOAD_URL}/${ETCD_VER}/etcd-${ETCD_VER}-linux-amd64.tar.gz &&\
    mkdir /tmp/etcd-download &&\
    tar xzf /tmp/etcd-${ETCD_VER}-linux-amd64.tar.gz -C /tmp/etcd-download --strip-components=1 &&\
    mv /tmp/etcd-download/etcd* /usr/local/bin/ && chmod 755 /usr/local/bin/* &&\
    rm -rf /tmp

ENV TZ=Asia/Shanghai\
    ETCD_DATA_DIR=/data\
    ETCD_LISTEN_CLIENT_URLS=http://0.0.0.0:2379\
    ETCD_LISTEN_PEER_URLS=http://0.0.0.0:2380\
    ETCD_ADVERTISE_CLIENT_URLS=http://0.0.0.0:2379\
    ETCD_INITIAL_ADVERTISE_PEER_URLS=http://0.0.0.0:2380\
    ETCD_INITIAL_CLUSTER='etcd=http://0.0.0.0:2380'

EXPOSE 2380 2379

CMD etcd

