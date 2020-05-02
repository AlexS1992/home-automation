FROM alpine:edge

RUN apk add --update --no-cache avahi && \
	sed -i 's/#enable-dbus=yes/enable-dbus=no/g' /etc/avahi/avahi-daemon.conf

VOLUME ["/etc/avahi/services"]
EXPOSE 5353/udp

ENTRYPOINT ["avahi-daemon"]

