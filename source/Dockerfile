FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    sudo \
    openssh-client \
    iproute2  \
    screen \
    sshpass \
    openssh-server \
    python3 python3-pip git \
    strace ltrace gdb gdbserver \
    sysstat dstat \
    curl wget unzip zip nano vim less \
    ca-certificates gnupg lsof \
    procps psmisc iproute2 net-tools \
    dnsutils iputils-ping traceroute \
    bash-completion locales tzdata \
    && \
    mkdir /var/run/sshd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Note: Historically, I didn't realize that ned was given "sudo" privelges, which messed up the whole chall.
# RUN useradd -m -s /bin/bash ned && \
#    echo 'ned:nedned' | chpasswd && \
#    usermod -aG sudo ned

# Notices that ned is no longer a sudoer here below
RUN useradd -m -s /bin/bash ned && \
    echo 'ned:nedned' | chpasswd && \
    usermod -aG ned

RUN useradd -m -s /bin/bash ned-stash && \
    echo 'ned-stash:zHqbRU.6*M91' | chpasswd && \
    usermod -aG sudo ned-stash

RUN sed -i 's/^#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Change user
USER ned
RUN mkdir -p /home/ned/.ssh
COPY --chown=ned-stash:ned-stash --chmod=600 flag.txt /home/ned-stash/flag.txt

# Adding a fake bash history
USER ned
RUN echo "history -c && history -w" >> /home/ned/.bash_history && \
    echo "mkdir preparing_for_athackctf" >> /home/ned/.bash_history && \
    echo "cd preparing_for_athackctf" >> /home/ned/.bash_history && \
    echo "git clone https://github.com/athack-ctf/How-To-Hack-2025-Challenges" >> /home/ned/.bash_history && \
    echo "cd How-To-Hack-2025-Challenges" >> /home/ned/.bash_history && \
    echo "ls" >> /home/ned/.bash_history && \
    echo "cat README.md" >> /home/ned/.bash_history && \
    echo "cd .." >> /home/ned/.bash_history && \
    echo "rm -rf ./How-To-Hack-2025-Challenges" >> /home/ned/.bash_history && \
    echo "exit" >> /home/ned/.bash_history
RUN chmod 600 /home/ned/.bash_history
EXPOSE 22

USER ned

RUN echo '#!/bin/bash' > /tmp/temp_script.sh && \
    echo 'screen -dmS stash && screen -S stash -X stuff "sshpass -p zHqbRU.6*M91 ssh -o StrictHostKeyChecking=no -tt ned-stash@localhost\\n"' >> /tmp/selfdestroy.sh && \
    echo 'rm -f /tmp/selfdestroy.sh' >> /tmp/selfdestroy.sh && \
    chmod +x /tmp/selfdestroy.sh
USER root

CMD service ssh start && su - ned -c /tmp/selfdestroy.sh && tail -f /dev/null
