FROM babim/alpinebase:3.8

## alpine linux
RUN apk add --no-cache wget bash && cd / && wget --no-check-certificate https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/option.sh && \
    chmod 755 /option.sh

ENV KB_VERSION 6.4.0
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

ENTRYPOINT ["/start.sh"]
CMD ["supervisord", "-nc", "/etc/supervisor/supervisord.conf"]