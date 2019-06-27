# https://github.com/elastic/logstash-docker
FROM docker.elastic.co/logstash/logstash:7.2.0

# Add your logstash plugins setup here
RUN logstash-plugin install logstash-filter-geoip
RUN logstash-plugin install logstash-filter-json
