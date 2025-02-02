FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    sudo \
    openssh-client \
    iproute2  \
    screen \
    vim \
    sshpass \
    openssh-server && \
    mkdir /var/run/sshd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash ned && \
    echo 'ned:password' | chpasswd && \
    usermod -aG sudo ned

RUN useradd -m -s /bin/bash superuser && \
    echo 'superuser:s3curep@55w0rd' | chpasswd && \
    usermod -aG sudo superuser

RUN sed -i 's/^#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
RUN sed -i 's/^#PubkeyAuthentication yes/PubkeyAuthentication yes/' /etc/ssh/sshd_config

# Change user
USER ned
RUN mkdir -p /home/ned/.ssh
COPY --chown=ned:ned --chmod=600 id_rsa /home/ned/.ssh/id_rsa
COPY --chown=ned:ned --chmod=644 id_rsa.pub /home/ned/.ssh/id_rsa.pub
COPY --chown=ned:ned --chmod=600 id_rsa.pub /home/ned/.ssh/authorized_keys
COPY --chown=superuser:superuser --chmod=600 flag.txt /home/superuser/flag.txt

EXPOSE 22

USER root
CMD service ssh start && su - ned -c 'screen -dmS sysadmin && screen -S sysadmin -X stuff "sshpass -p s3curep@55w0rd ssh -o StrictHostKeyChecking=no -tt superuser@localhost\\n"' && tail -f /dev/null