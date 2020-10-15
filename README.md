# MOVED TO GITLAB

# docker-logcollector

Receive rsyslogs, store in Elasticsearch, show in Kibana or Grafana.

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
    
## Curator cron job
    # Run every 10 minutes
    */10 * * * * cd /opt/docker-logcollector && /usr/local/bin/docker-compose run --rm curator --config config.yml action-file.yml > /dev/null

## Custom containers on dockerhub

naturalis/rsyslog:0.0.1 , Dockerfile in rsyslog dir: 
build using
```
sudo docker build -t naturalis/rsyslog:0.0.1
```

naturalis/logstash:7.3.2 , Dockerfile in logstash
Tag follows ELK_VERSION, build using --build-arg like below
```
sudo docker build -t naturalis/logstash:7.3.2 . --build-arg ELK_VERSION=7.3.2
```
