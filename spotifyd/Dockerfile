FROM centos:8

ENV SPOTIFYD_VERSION 0.2.24

RUN yum update -y && yum install -y wget alsa-lib-devel openssl-devel alsa-utils

RUN set -ex \
	&& wget -O spotifyd.tar.gz https://github.com/Spotifyd/spotifyd/releases/download/v0.2.20/spotifyd-linux-full.tar.gz \
	&& mkdir -p /var/spotifyd \
	&& tar -xf spotifyd.tar.gz  -C /var/spotifyd \
	&& rm spotifyd.tar.gz 

COPY spotifyd.conf /etc/spotifyd.conf

COPY asound.conf /etc/asound.conf

CMD /var/spotifyd/spotifyd --no-daemon
