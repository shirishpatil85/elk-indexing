# Sprin Boot ELK example

* Dockered Spring Boot App
  * logback-spring.xml configured using LogstashTcpSocketAppender to transfer log statements to a logstash instance
  * executed in a Docker container
* ELK Docker container
  * Logstash
    * receiving log statements from the spring boot app via tcp
    * persisting them in elasticsearch
  * Elasticsearch
    * [indexed log store](http://localhost:9200/_search?pretty)
  * Kibana
    * [Dashboard](http://localhost:5601/app/kibana) to discover log data stored in elasticsearch
* All containers linked via Docker network

## Overview
  
![alt text][overview]

[overview]: doc/docker-overview.png "Architectural overview"

## How to run it?
1. build the docker images by executing `mvn clean install`
2. startup Docker containers by executing `docker-compose up`
3. create an index pattern, f.e. `logstash-*`, in [Kibana dashboard](http://localhost:5601/app/kibana)


# Gitpod steps (non docker setup)

## Install elk

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.13.2-linux-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.13.2-linux-x86_64.tar.gz.sha512
shasum -a 512 -c elasticsearch-7.13.2-linux-x86_64.tar.gz.sha512 
tar -xzf elasticsearch-7.13.2-linux-x86_64.tar.gz
cd elasticsearch-7.13.2/bin
./elasticsearch -d -p pid

curl -O https://artifacts.elastic.co/downloads/kibana/kibana-7.13.2-darwin-x86_64.tar.gz
curl https://artifacts.elastic.co/downloads/kibana/kibana-7.13.2-darwin-x86_64.tar.gz.sha512 | shasum -a 512 -c - 
tar -xzf kibana-7.13.2-darwin-x86_64.tar.gz
cd kibana-7.13.2-darwin-x86_64/
./bin/kibana &

wget https://artifacts.elastic.co/downloads/logstash/logstash-7.13.2-linux-x86_64.tar.gz
tar -xzf logstash-7.13.2-linux-x86_64.tar.gz
cd logstash-7.13.2
./bin/logstash -f logstash.conf  //change conf file before starting


mvn spring-boot:run