# fl0r3k/prometheus:2.34.0

FROM fl0r3k/streaming-base

ARG PROMETHEUS_VERSION=2.34.0
ARG PROMETHEUS_HOME=/usr/local/prometheus
ARG PROMETHEUS_ARCHIVE_NAME=prometheus-${PROMETHEUS_VERSION}.linux-amd64

RUN wget -P /tmp/ https://github.com/prometheus/prometheus/releases/download/v${PROMETHEUS_VERSION}/${PROMETHEUS_ARCHIVE_NAME}.tar.gz && \
    tar xvfz /tmp/${PROMETHEUS_ARCHIVE_NAME}.tar.gz -C /tmp && \
    mv /tmp/${PROMETHEUS_ARCHIVE_NAME} ${PROMETHEUS_HOME}

ENV PATH=${PATH}:${KAFKA_HOME}/bin

EXPOSE 9092

COPY jmx_prometheus_kafka.yml ${PROMETHEUS_AGENT_HOME}
COPY server.properties.template ${KAFKA_HOME}/config
COPY start.sh .

ENTRYPOINT ["./start.sh"]