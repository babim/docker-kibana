FROM babim/alpinebase

ENV GOSU_VERSION 1.9

# download tool
RUN apk add --update curl ca-certificates

# Install NodeJS
RUN apk add --update nodejs

COPY docker-entrypoint.sh /usr/share/kibana/docker-entrypoint.sh
RUN chmod +x /usr/share/kibana/docker-entrypoint.sh

RUN curl -o /usr/local/bin/gosu -sSL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64" && \
    chmod +x /usr/local/bin/gosu

EXPOSE 5601

ENTRYPOINT ["/usr/share/kibana/docker-entrypoint.sh"]
#CMD ["kibana", "-c", "/usr/share/kibana/config/kibana.yml"]
