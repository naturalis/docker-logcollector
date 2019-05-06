# docker-flekgt

filebeat - logstash - elasticsearch - kibana - grafana - traefik

## pfSense


## Cumulus

cp cumulus.env .env

## Delete indexes
    docker-compose exec elasticsearch sh
    curl -XDELETE elasticsearch:9200/logstash-*
