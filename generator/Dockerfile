FROM golang:latest

RUN apt-get update && apt-get install -y libsnmp-dev

COPY . /go/src/github.com/prometheus/snmp_exporter/
RUN cd /go/src/github.com/prometheus/snmp_exporter/generator \
    go get -v . && \
    go install

# Move the default generator file to the expected location
RUN cp /go/src/github.com/prometheus/snmp_exporter/generator/generator.yml /opt/

WORKDIR "/opt"

ENTRYPOINT ["/go/bin/generator"]

CMD ["generate"]
