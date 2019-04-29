FROM babim/kibana:base

ENV KB_VERSION 7.0.0
ENV KIBANA 7
ENV SOFT kibana
ENV BIT x86_64
ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/kibana"
ENV TARBAL "${DOWNLOAD_URL}/kibana-oss-${KB_VERSION}-linux-${BIT}.tar.gz"


# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/${SOFT}_install.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601
