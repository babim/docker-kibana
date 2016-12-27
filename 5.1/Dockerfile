FROM babim/kibana:base

# Kibana version
ENV KIBANA_VERSION=5.1.1

RUN curl -LO https://download.elasticsearch.org/kibana/kibana/kibana-${KIBANA_VERSION}-linux-x64.tar.gz && \
    tar xzf /kibana-${KIBANA_VERSION}-linux-x64.tar.gz -C / && \
    mv /kibana-${KIBANA_VERSION}-linux-x64 /usr/share/kibana && \
    rm /usr/share/kibana/node/bin/node && \
    rm /usr/share/kibana/node/bin/npm && \
    ln -s /usr/bin/node /usr/share/kibana/node/bin/node && \
    ln -s /usr/bin/npm /usr/share/kibana/node/bin/npm && \
    rm -rf /var/cache/apk/* /kibana-${KIBANA_VERSION}-linux-x64.tar.gz

COPY kibana.yml /usr/share/kibana/config/kibana.yml

# clean
RUN apk del curl ca-certificates