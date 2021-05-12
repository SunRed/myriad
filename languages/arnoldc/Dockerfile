FROM openjdk:17-alpine
LABEL author="SunRed"

RUN apk add --no-cache curl && \
    curl -O http://lhartikk.github.io/ArnoldC.jar && \
    mv ArnoldC.jar /var/run && \
    apk del --no-cache curl

COPY run.sh /var/run/
