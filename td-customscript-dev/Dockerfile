FROM digdag/digdag-python:3.7.3-stretch

ENV HOME /home/td-user
ENV HOME_SETUP ${HOME}/git/setup-local

USER root
RUN apt-get update
RUN apt-get install -y vim git

USER td-user
RUN     git clone https://github.com/waysaku/setup-local.git ${HOME_SETUP}
WORKDIR ${HOME_SETUP}
RUN     bash ./setup.sh

WORKDIR ${HOME}
