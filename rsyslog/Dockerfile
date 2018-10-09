FROM alpine

RUN apk add --no-cache rsyslog

EXPOSE 514/tcp 514/udp
ENTRYPOINT ["rsyslogd", "-n", "-f", "/etc/rsyslogd.conf"]
