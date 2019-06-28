# docker-flekgt

filebeat - logstash - elasticsearch - kibana - grafana - traefik

## Needed for Elasticsearch
    echo 'vm.max_map_count=262144' >> /etc/sysctl.conf

## pfSense/OPNsense
    cp pfsense.env .env

## Cumulus
    cp cumulus.env .env

## Delete indexes
    docker-compose exec elasticsearch sh
    curl -XDELETE elasticsearch:9200/logstash-*

## Curator
    docker-compose run --rm curator --config config.yml action-file.yml
    
# Curator cron job    
    * * * * * cd /opt/docker-flekgt && /usr/local/bin/docker-compose run --rm curator --config config.yml action-file.yml >> /var/log/cron.log
