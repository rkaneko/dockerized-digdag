FROM openjdk:8-jdk
MAINTAINER rkaneko<kanek.o.dev@gmail.com>

# see also http://docs.digdag.io/releases.html
ARG DIGDAG_VERSION
ENV DIGDAG_VERSION=${DIGDAG_VERSION:-"0.9.19"}

RUN apt-get update && apt-get install -y \
        curl \
        build-essential \
        python3 \
        python3-dev \
        python3-pip \
        && rm -rf /var/lib/apt/lists/* \
        && cd "$(dirname $(which python3))" \
        && ln --force -s pydoc3 pydoc \
        && ln --force -s python3 python \
        && ln --force -s python3-config python-config \
        && ln --force -s pip3 pip

RUN curl -o /usr/bin/digdag --create-dirs -L "https://dl.digdag.io/digdag-${DIGDAG_VERSION}" \
        && chmod +x /usr/bin/digdag \
        && adduser --gecos 'digdag user' --shell /sbin/nologin --disabled-password --no-create-home digdag \
        && mkdir -p /etc/digdag /var/log/digdag/server /var/log/digdag/tasks \
        && chown -R digdag.digdag /etc/digdag \
        && chown -R digdag.digdag /var/log/digdag

COPY docker/digdag/digdag.properties /etc/digdag/digdag.properties

USER digdag

WORKDIR /etc/digdag

CMD ["sh", "-c", "digdag", "--help"]
