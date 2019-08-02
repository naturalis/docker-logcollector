# docker-logcollector

## Needed for Elasticsearch
    echo 'vm.max_map_count=262144' >> /etc/sysctl.conf

## OPNsense
    cp opnsense.env .env

## Cumulus
    cp cumulus.env .env

## Delete indexes
    docker-compose exec elasticsearch sh
    curl -XDELETE elasticsearch:9200/logstash-*

## Run Curator manually
    docker-compose run --rm curator --config config.yml action-file.yml
    
### Curator cron job
    # Run every 10 minutes
    */10 * * * * cd /opt/docker-logcollector && /usr/local/bin/docker-compose run --rm curator --config config.yml action-file.yml > /dev/null
