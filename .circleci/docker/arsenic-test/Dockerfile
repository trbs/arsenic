FROM ubuntu:zesty

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
  apt-get install -y software-properties-common && \
  add-apt-repository ppa:mozillateam/firefox-next && \
  apt-get update && \
  apt-get install -y \
    xvfb \
    python3.6 \
    python3.6-venv \
    python3.6-dev \
    build-essential \
    wget \
    firefox

ARG GECKODRIVER_VERSION=0.16.1

RUN wget --no-verbose -O /tmp/geckodriver.tar.gz https://github.com/mozilla/geckodriver/releases/download/v$GECKODRIVER_VERSION/geckodriver-v$GECKODRIVER_VERSION-linux64.tar.gz \
  && rm -rf /opt/geckodriver \
  && tar -C /opt -zxf /tmp/geckodriver.tar.gz \
  && rm /tmp/geckodriver.tar.gz \
  && mv /opt/geckodriver /opt/geckodriver-$GECKODRIVER_VERSION \
  && chmod 755 /opt/geckodriver-$GECKODRIVER_VERSION \
  && ln -fs /opt/geckodriver-$GECKODRIVER_VERSION /usr/local/bin/geckodriver
