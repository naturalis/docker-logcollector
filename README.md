# docker-flekgt

filebeat - logstash - elasticsearch - kibana - grafana - traefik

## Needed for Elasticsearch
    echo 'vm.max_map_count=262144' >> /etc/sysctl.conf


## pfSense


## Cumulus

cp cumulus.env .env

## Delete indexes
    docker-compose exec elasticsearch sh
    curl -XDELETE elasticsearch:9200/logstash-*

