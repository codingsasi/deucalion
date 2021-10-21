FROM golang:1.17.1-alpine3.14

COPY config/prometheus.yml /prometheus.yml

RUN apk update \
    && apk upgrade \
    && apk add git make bash npm nodejs curl

RUN  cd /opt \
    && git clone https://github.com/prometheus/prometheus.git \
    && cd prometheus && git checkout v2.30.1 \
    && make build

RUN ln -sf /opt/prometheus/conf /etc/prometheus
RUN ln -sf /opt/prometheus/data /prometheus

ENTRYPOINT [ "/opt/prometheus/prometheus" ]
CMD [ "--config.file=/prometheus.yml" ]
