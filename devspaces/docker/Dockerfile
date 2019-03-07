FROM ubuntu:18.04

LABEL description="This file generates a docker image containing everything needed to build and run Phoenix-Trello application"

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y wget \
    build-essential \
    postgresql \
    postgresql-contrib \
    curl \
    mc \
    dialog \
    git && \
    wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && \
    dpkg -i erlang-solutions_1.0_all.deb && \
    curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get update && \
    apt-get -y install esl-erlang elixir nodejs git && \
    update-rc.d postgresql enable && \
    apt-get clean   

ENV LANG=C.UTF-8

USER postgres
RUN service postgresql start && psql -c "ALTER USER postgres PASSWORD 'postgres';"
USER root

WORKDIR /data

CMD service postgresql start && tail -f /dev/null
