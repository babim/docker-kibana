FROM babim/alpinebase

ENV GOSU_VERSION 1.9

# download tool
RUN apk add --no-cache curl ca-certificates

# Install NodeJS
RUN apk add --no-cache nodejs

COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh

RUN curl -o /usr/local/bin/gosu -sSL "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64" && \
    chmod +x /usr/local/bin/gosu

EXPOSE 5601

ENTRYPOINT ["/docker-entrypoint.sh"]
#CMD ["kibana", "-c", "/usr/share/kibana/config/kibana.yml"]
