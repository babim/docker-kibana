FROM babim/kibana:base

# Kibana version
ENV KB_VERSION=4.3.0
ENV KIBANA 4
ENV DOWNLOAD_URL "https://download.elastic.co/kibana/kibana"
ENV BIT x64
ENV TARBAL "${DOWNLOAD_URL}/kibana-${KB_VERSION}-linux-${BIT}.tar.gz"

# install
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_install.sh | bash
# remove packages
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_clean.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601

#ENTRYPOINT ["/start.sh"]
#CMD ["kibana"]
CMD ["/sbin/tini","--","/usr/bin/supervisord","-c", "/etc/supervisor/supervisord.conf"]