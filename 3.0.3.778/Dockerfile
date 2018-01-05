FROM anapsix/alpine-java:8u152b16_server-jre as dependencies

ENV SCANNER_VERSION=3.0.3.778

RUN apk update
RUN apk add \
  curl \
  unzip

WORKDIR /tmp
RUN curl -sLO https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SCANNER_VERSION}.zip
RUN unzip sonar-scanner-cli-${SCANNER_VERSION}.zip
RUN mv sonar-scanner-${SCANNER_VERSION} sonar-scanner



FROM anapsix/alpine-java:8u152b16_server-jre as runtime

COPY --from=dependencies /tmp/sonar-scanner /usr/local/sonar-scanner

RUN \
  apk update && \
  apk add \
    git \
    nodejs \
    python \
    yarn \
    && \
  mkdir /project

WORKDIR /project

ENV PATH=${PATH}:/usr/local/sonar-scanner/bin

CMD ["sonar-scanner"]
