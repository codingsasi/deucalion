FROM golang:1.17.1-alpine3.14

WORKDIR /prometheus

RUN mkdir /etc/prometheus

RUN apk update \
    && apk upgrade \
    && apk add git make bash npm nodejs curl \
    && npm -g install npm

RUN  cd /opt \
    && git clone https://github.com/prometheus/prometheus.git \
    && cd prometheus && git checkout v2.30.1 \
    && make build

RUN cp /opt/prometheus/prometheus /bin/prometheus && cp /opt/prometheus/promtool /bin/promtool

RUN ln -s /opt/prometheus/console_libraries /opt/prometheus/consoles/ /etc/prometheus/ && \
    chown -R nobody:nobody /etc/prometheus

COPY prom/prometheus.yml prometheus.yml
RUN cat prometheus.yml
ENTRYPOINT [ "prometheus" ]
