# This file is not in use. It's only here for testing and trying to compile prometheus from source.
FROM golang:1.17.1-alpine3.14

WORKDIR /prometheus

RUN mkdir /etc/prometheus

COPY prometheus.yml /etc/prometheus/prometheus.yml
COPY web.yml /etc/prometheus/web.yml

RUN apk update \
    && apk upgrade \
    && apk add git make bash npm nodejs curl \
    && npm -g install npm \
    && node -v && npm -v

RUN  cd /opt \
    && git clone https://github.com/prometheus/prometheus.git \
    && cd prometheus && git checkout v2.39.1 \
    && make build

RUN cp /opt/prometheus/prometheus /bin/prometheus && cp /opt/prometheus/promtool /bin/promtool

RUN ln -s /opt/prometheus/console_libraries /opt/prometheus/consoles/ /etc/prometheus/ && \
    chown -R nobody:nobody /etc/prometheus

ENTRYPOINT [ "prometheus" ]
