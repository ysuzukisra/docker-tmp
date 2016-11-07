FROM debian

RUN apt-get update \
    && apt-get install -y locales curl wget git ca-certificates vim openssh-server --no-install-recommends \
    && apt-get clean \
    && rm -rf /var/cache/apt/archives/*

RUN echo en_US.UTF-8 UTF-8 > /etc/locale.gen \
    && locale-gen \
    && update-locale LANG=en_US.UTF-8 \
    && export LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8 \
    && sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config \
    && sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
    && sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config \
    && echo root:root | chpasswd \

ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8
EXPOSE 22
CMD service ssh start && tail -f /dev/null
