FROM babim/kibana:base

# Kibana version
ENV KB_VERSION=4.0.3
ENV KIBANA 4
ENV DOWNLOAD_URL "https://download.elastic.co/kibana/kibana"
ENV BIT x64
ENV TARBAL "${DOWNLOAD_URL}/kibana-${KB_VERSION}-linux-${BIT}.tar.gz"

# install
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_install.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601
