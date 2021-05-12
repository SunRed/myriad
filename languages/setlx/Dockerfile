FROM openjdk:17-alpine
LABEL author="SunRed"

COPY setlX /usr/local/bin/
COPY run.sh /var/run/

RUN apk add --no-cache curl unzip bash && \
    curl -O https://download.randoom.org/setlX/pc/setlX_v2-7-2.binary_only.zip && \
    unzip -d setlx setlX_v2-7-2.binary_only.zip && \
    rm -f setlX_v2-7-2.binary_only.zip && \
    mkdir -p /usr/local/setlX && \
    mv setlx/setlX*.jar /usr/local/setlX && \
    mkdir -p /usr/local/setlXlibrary && \
    mv setlx/setlXlibrary/* /usr/local/setlXlibrary && \
    chmod +x /usr/local/bin/setlX && \
    rm -rf setlx && \
    apk del --no-cache curl unzip
