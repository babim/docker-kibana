# Kibana
Thanks Portefaix and blacktop

[Alpine Linux][https://alpinelinux.org/] is a Linux distribution built around musl libc and BusyBox.
This image is based on the official Alpine Linux.

[Kibana][https://www.elastic.co/products/kibana] is an open source data visualization platform.
Port exported is : `5601`

## Usage

You could check *elasticsearch* on : `http://localhost:9200` and Kibana running on `http://localhost:5601/status`

Don't use tag :base OK ? :-)

## Getting Started
```
$ docker run --init -d --name elasticsearch -p 9200:9200 babim/elasticsearch
$ docker run --init -d --name kibana --link elasticsearch -p 5601:5601 babim/kibana
```

## Customize at runtime via environment variables
There are two types of env vars:

`KIBANA_ELASTICSEARCH_URL=http://localhost:9200`
`elasticsearch.url=http://localhost:9200`

To use your own elasticsearch address via KIBANA_ELASTICSEARCH_URL
```
$ docker run --init -d --name kibana -e KIBANA_ELASTICSEARCH_URL=http://some-elasticsearch:9200 -p 5601:5601 babim/kibana
```
For elasticsearch running on a OSX host it would be
```
$ docker run --init -d --name kibana \
  -p 5601:5601 \
  --net host \
  -e KIBANA_ELASTICSEARCH_URL="http://$(ipconfig getifaddr en0):9200" \
  babim/kibana
```

## For x-pack with basic auth:
```
$ docker run --init -d --name kibana \
             --restart unless-stopped \
             -p 443:5601 \
             -v /etc/letsencrypt/archive/demo.malice.io:/certs \
             -e KIBANA_SERVER_SSL_ENABLED=true \
             -e KIBANA_SERVER_SSL_KEY=/certs/privkey1.pem \
             -e KIBANA_SERVER_SSL_CERTIFICATE=/certs/cert1.pem \
             -e KIBANA_ELASTICSEARCH_URL=$KIBANA_ELASTICSEARCH_URL \
             -e KIBANA_ELASTICSEARCH_USERNAME=$KIBANA_ELASTICSEARCH_USERNAME \
             -e KIBANA_ELASTICSEARCH_PASSWORD=$KIBANA_ELASTICSEARCH_PASSWORD \
             babim/kibana:x-pack
```