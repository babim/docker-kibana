FROM babim/alpinebase:3.8

## alpine linux
RUN apk add --no-cache curl bash && \
	curl https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20SCRIPT%20AUTO/option.sh -o /option.sh && \
	chmod 755 /option.sh

ENV KB_VERSION 6.4.3
ENV KIBANA 6
ENV DOWNLOAD_URL "https://artifacts.elastic.co/downloads/kibana"
ENV TARBAL "${DOWNLOAD_URL}/kibana-${KB_VERSION}-linux-x86_64.tar.gz"
ENV SOFT kibana

# install
RUN curl -s https://raw.githubusercontent.com/babim/docker-tag-options/master/z%20ElasticStack%20install/${SOFT}_install.sh | bash

WORKDIR /usr/share/kibana

ENV PATH /usr/share/kibana/bin:$PATH

EXPOSE 5601

ENTRYPOINT ["/start.sh"]
CMD ["kibana"]
#CMD ["/sbin/tini","--","/usr/bin/supervisord","-c", "/etc/supervisor/supervisord.conf"]