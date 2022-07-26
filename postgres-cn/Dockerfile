FROM postgres:11-alpine

ARG VER_GLIBC=2.35-r0 GITHUB_URL=https://hub.fastgit.xyz

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.huaweicloud.com/g' /etc/apk/repositories &&\
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub &&\
    wget -q -O /tmp/glibc.apk ${GITHUB_URL}/sgerrand/alpine-pkg-glibc/releases/download/${VER_GLIBC}/glibc-${VER_GLIBC}.apk &&\
    wget -q -O /tmp/glibc-bin.apk ${GITHUB_URL}/sgerrand/alpine-pkg-glibc/releases/download/${VER_GLIBC}/glibc-bin-${VER_GLIBC}.apk &&\
    wget -q -O /tmp/glibc-i18n.apk ${GITHUB_URL}/sgerrand/alpine-pkg-glibc/releases/download/${VER_GLIBC}/glibc-i18n-${VER_GLIBC}.apk &&\
    apk add --no-cache tzdata /tmp/glibc.apk /tmp/glibc-bin.apk /tmp/glibc-i18n.apk &&\
    rm -rf /tmp/* &&\
    /usr/glibc-compat/bin/localedef -i zh_CN -f UTF-8 zh_CN.UTF-8

ENV LANG=zh_CN.UTF-8 LANGUAGE=zh_CN.UTF-8 TZ=Asia/Shanghai
