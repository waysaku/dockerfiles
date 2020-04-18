FROM ubuntu:latest

ENV USER waysaku
ENV HOME /home/waysaku
ENV HOME_SETUP ${HOME}/git/setup-local

RUN useradd -m ${USER}
RUN gpasswd -a ${USER} sudo
RUN echo "${USER}:pass_waysaku" | chpasswd

USER root
RUN apt-get update
RUN apt-get install -y vim git sudo gnupg curl locales

RUN locale-gen en_US.UTF-8
RUN update-locale
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# Install TD toolbelt
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 901F9177AB97ACBE
RUN curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh

USER ${USER}
RUN     git clone https://github.com/waysaku/setup-local.git ${HOME_SETUP}
WORKDIR ${HOME_SETUP}
RUN     bash ./setup.sh

WORKDIR ${HOME}
