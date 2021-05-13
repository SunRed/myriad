FROM alpine as build

RUN apk add --no-cache build-base git cmake

WORKDIR /tmp/lci
RUN git clone https://github.com/justinmeza/lci.git .

RUN cmake . && make


FROM alpine
LABEL author="SunRed"

COPY --from=build /tmp/lci/lci /usr/local/bin
COPY run.sh /var/run/
