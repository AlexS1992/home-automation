FROM alpine:edge

RUN set -ex \
	&& adduser --uid 321 -S snapcast -G audio \
	&& mkdir -p /tmp/soundshare \
	&& chown -R snapcast:audio /tmp/soundshare \
	&& chmod 0777 /tmp/soundshare

VOLUME ["/tmp/soundshare"]

USER snapcast

RUN mkfifo /tmp/soundshare/snapfifo

CMD ["true"]
