FROM babim/kibana:base

ENV KB_VERSION 6.1.4
ENV KIBANA 6
ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/kibana"
ENV TARBAL "${DOWNLOAD_URL}/kibana-${KB_VERSION}-linux-x86_64.tar.gz"

# install
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_install.sh | bash
# remove packages
RUN wget --no-check-certificate -O - https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/kibana_clean.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601

#ENTRYPOINT ["/start.sh"]
#CMD ["kibana"]
CMD ["supervisord", "-nc", "/etc/supervisor/supervisord.conf"]