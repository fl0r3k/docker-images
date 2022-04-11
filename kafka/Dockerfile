# fl0r3k/kaka:3.1.0

FROM fl0r3k/streaming-base

ARG KAFKA_VERSION=3.1.0
ARG SCALA_VERSION=2.13
ARG KAFKA_HOME=/usr/local/kafka
ARG KAFKA_ARCHIVE_NAME=kafka_${SCALA_VERSION}-${KAFKA_VERSION}

RUN wget -P /tmp/ https://archive.apache.org/dist/kafka/${KAFKA_VERSION}/${KAFKA_ARCHIVE_NAME}.tgz && \
    tar -zvxf /tmp/${KAFKA_ARCHIVE_NAME}.tgz -C /tmp && \
    mv /tmp/${KAFKA_ARCHIVE_NAME} ${KAFKA_HOME} && \
    mkdir /tmp/kafka-logs

ENV KAFKA_VERSION=${KAFKA_VERSION} \
    KAFKA_HOME=${KAFKA_HOME}

ENV PATH=${PATH}:${KAFKA_HOME}/bin

EXPOSE 9092

COPY server.properties.template ${KAFKA_HOME}/config
COPY start.sh .

ENTRYPOINT ["./start.sh"]