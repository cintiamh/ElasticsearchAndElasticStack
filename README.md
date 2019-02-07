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

```
$ wget http://media.sundog-soft.com/es6/shakes-mapping.json
$ curl -H "Content-Type: application/json" -XPUT 127.0.0.1:9200/shakespeare --data-binary @shakes-mapping.json
```