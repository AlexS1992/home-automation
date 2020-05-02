FROM alpine:edge

ENV SNAPCAST_VERSION 0.19.0

RUN apk update && apk upgrade

RUN apk add --no-cache wget g++ make alsa-lib alsa-utils avahi-dev libvorbis-dev opus-dev flac-dev \
	boost expat bash asio-dev libogg-dev soxr

RUN set -ex \
	&& wget -O snapcast.tar.gz https://github.com/badaix/snapcast/archive/v0.19.0.tar.gz \
	&& mkdir /usr/local/snapcast \
	&& tar -xzC /usr/local/snapcast --strip-components=1 -f snapcast.tar.gz \
	&& rm snapcast.tar.gz

RUN cd /usr/local/snapcast/server && make

RUN adduser --uid 321 -S snapcast -G audio --home /home/snapcast \
	&& mkdir -p /home/snapcast/.config \
	&& chown snapcast:audio -R /home/snapcast

USER snapcast

COPY snapserver.conf /etc/snapserver.conf

EXPOSE 1704
EXPOSE 1705
EXPOSE 1780

ENTRYPOINT ["/usr/local/snapcast/server/snapserver"]
