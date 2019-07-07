FROM alpine:3.8 AS build

ENV RABBITMQ_DELAYED_MESSAGE_URL "https://dl.bintray.com/rabbitmq/community-plugins/3.7.x/rabbitmq_delayed_message_exchange/rabbitmq_delayed_message_exchange-20171201-3.7.x.zip"

RUN set -eux; \
        \
        apk add --no-cache \
            curl \
            unzip \
            tzdata \
        ; \
        curl $RABBITMQ_DELAYED_MESSAGE_URL > /tmp/rabbitmq_delayed_message_exchange-20171201-3.7.x.zip; \
        unzip -d /tmp /tmp/rabbitmq_delayed_message_exchange-20171201-3.7.x.zip; \
        echo "America/Sao_Paulo" > /etc/timezone

FROM rabbitmq:3.7.15-alpine

LABEL maintainer "Daniel Vincenzi <danielvincenzi@icloud.com>"

COPY --from=build /tmp/rabbitmq_delayed_message_exchange-20171201-3.7.x.ez /opt/rabbitmq/plugins
COPY --from=build /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
COPY --from=build /etc/timezone /etc/timezone
