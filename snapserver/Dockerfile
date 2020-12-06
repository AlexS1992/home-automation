FROM alpine:edge

RUN apk update && apk upgrade

RUN apk add --no-cache snapcast-server asio soxr

USER snapcast

COPY snapserver.conf /etc/snapserver.conf

EXPOSE 1704
EXPOSE 1705
EXPOSE 1780

ENTRYPOINT ["snapserver"]
