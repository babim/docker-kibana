FROM babim/kibana:base

# Kibana version
ENV KIBANA_VERSION=4.5.0
ENV KIBANA 4
ENV DOWNLOAD_URL "https:///download.elasticsearch.org/kibana/kibana"
ENV BIT x64
ENV TARBAL "${DOWNLOAD_URL}/kibana-${KIBANA_VERSION}-linux-${BIT}.tar.gz"

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_install.sh | bash
# remove packages
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_clean.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601

ENTRYPOINT ["/start.sh"]
CMD ["kibana"]
