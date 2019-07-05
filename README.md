# docker-logcollector

filebeat - logstash - elasticsearch - kibana - grafana - traefik

## Needed for Elasticsearch
    echo 'vm.max_map_count=262144' >> /etc/sysctl.conf

## OPNsense
    cp opnsense.env .env

## Cumulus
    cp cumulus.env .env

## Delete indexes
    docker-compose exec elasticsearch sh
    curl -XDELETE elasticsearch:9200/logstash-*

## Curator
    docker-compose run --rm curator --config config.yml action-file.yml
    
### Curator cron job
    # Run every 10 minutes
    */10 * * * * cd /opt/docker-flekgt && /usr/local/bin/docker-compose run --rm curator --config config.yml action-file.yml > /dev/null

### Rsyslog cron job
    # Delete syslog file every midnight
    0 0 * * * cd /opt/docker-flekgt && /usr/local/bin/docker-compose exec rsyslog rm /var/log/syslog && /usr/local/bin/docker-compose restart rsyslog >> /var/log/cron.log
