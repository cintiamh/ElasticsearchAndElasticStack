# Elasticsearch And Elastic Stack

## Setting up with Docker

List of existing Docker images: https://www.docker.elastic.co/

Elasticsearch Docker container

```
$ docker pull docker.elastic.co/elasticsearch/elasticsearch:6.6.0
$ docker run -d -p 9200:9200 -p 9300:9300 -it -h elasticsearch --name elasticsearch docker.elastic.co/elasticsearch/elasticsearch:6.6.0
$ curl http://localhost:9200
```

Kibana

```
$ docker pull docker.elastic.co/kibana/kibana:6.6.0
$ docker run -d -p 5601:5601 -h kibana --name kibana --link elasticsearch:elasticsearch docker.elastic.co/kibana/kibana:6.6.0
```

You can check Kibana at http://localhost:5601.

Install the Shakespeare search index in Elasticsearch 6

```
$ wget http://media.sundog-soft.com/es6/shakes-mapping.json
$ curl -H 'Content-Type: application/json' -XPUT 127.0.0.1:9200/shakespeare --data-binary @shakes-mapping.json
$ wget http://media.sundog-soft.com/es6/shakespeare_6.0.json
$ curl -H 'Content-Type: application/json' -XPOST 'localhost:9200/shakespeare/doc/_bulk?pretty' --data-binary  @shakespeare_6.0.json    
$ curl -H 'Content-Type: application/json' -XGET '127.0.0.1:9200/shakespeare/_search?pretty' -d '
>>> {
>>> "query" : {
>>> "match_phrase" : {
>>> "text_entry" : "to be or not to be"
>>> }
>>> }
>>> }
>>> '
```

### Elasticsearch Overview
