FROM alpine:3.5

LABEL Author=voidint
LABEL Email=voidint@126.com

ARG OS=linux
ARG ARCH=amd64
ARG RELEASE_VERSION=1.0.1

ENV SWAGGER_HUB_HOME /opt/swagger-hub
ENV SWAGGER_HUB_BIN /opt/bin
ENV UI_DOWNLOAD_URL https://github.com/voidint/swagger-hub/raw/master/releases/swagger-hub-ui.tar.gz
ENV SERVER_DOWNLOAD_URL "https://github.com/voidint/swagger-hub/raw/master/releases/doc-server-$RELEASE_VERSION-$OS-$ARCH.tar.gz"

RUN apk update \
    && apk add ca-certificates wget \
    && mkdir -p "$SWAGGER_HUB_HOME" "$SWAGGER_HUB_BIN" \
    && wget -O "$SWAGGER_HUB_HOME/swagger-hub-ui.tar.gz" "$UI_DOWNLOAD_URL" \
    && wget -O "$SWAGGER_HUB_HOME/doc-server.tar.gz" "$SERVER_DOWNLOAD_URL" \
    && tar -xz -f "$SWAGGER_HUB_HOME/doc-server.tar.gz" -C "$SWAGGER_HUB_BIN" \
    && tar -xz -f "$SWAGGER_HUB_HOME/swagger-hub-ui.tar.gz" -C "$SWAGGER_HUB_HOME" \
    && chown -R root:root /opt/* \
    && chmod u+x "$SWAGGER_HUB_BIN/doc-server" \
    && rm -f "$SWAGGER_HUB_HOME/doc-server.tar.gz" "$SWAGGER_HUB_HOME/swagger-hub-ui.tar.gz" 

ENV PATH "$PATH:$SWAGGER_HUB_BIN"

WORKDIR $SWAGGER_HUB_HOME

EXPOSE 8080

ENTRYPOINT ["doc-server", "run", "--dir", "/opt/swagger-hub/web"]
