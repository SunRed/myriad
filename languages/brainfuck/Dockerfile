FROM alpine as build

WORKDIR /tmp/bf
RUN apk add --no-cache musl-dev gcc make git && \
    git clone https://github.com/rdebath/Brainfuck.git . && \
    cd tritium && \
    make

FROM alpine
LABEL author="SunRed"

COPY --from=build /tmp/bf/tritium/bfi.out /usr/local/bin/bf
COPY run.sh /var/run/
