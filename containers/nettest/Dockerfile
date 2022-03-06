FROM ubuntu:20.04

LABEL maintainer "Mike Pfeiffer <mic54@protonmail.com>"

ARG USER
ARG PSWD

ENV USER ${USER}
ENV PSWD ${PSWD}

WORKDIR /home

RUN apt-get update

# install network services
RUN apt-get install -y nmap vim fping wget curl \
    iputils-ping traceroute dnsutils iproute2 net-tools

# install ssh service and user
RUN apt-get install -y sudo openssh-server
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 ${USER}
RUN echo ${USER}:${PSWD} | chpasswd
RUN service ssh start

CMD ["/usr/sbin/sshd","-D"]
