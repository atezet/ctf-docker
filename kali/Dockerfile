FROM kalilinux/kali-rolling

RUN apt update && \
  apt upgrade -y && \
  apt install -y \
    locales \
    net-tools \
    psmisc \
    python3-pip \
    tmux \
    zsh && \
  apt install -y \
    dnsutils \
    exploitdb \
    exploitdb-bin-sploits \
    netcat-traditional \
    nmap \
    metasploit-framework \
    sqlmap \
    windows-binaries \
    wordlists \
  && apt clean

RUN pip3 install impacket \
    virtualenv

RUN mkdir -p /root
RUN chsh -s /usr/bin/zsh && \
    wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | /usr/bin/zsh || true

# https://stackoverflow.com/a/28406007/2961949
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

COPY msfconsole.rc /root/.msf4/msfconsole.rc
COPY database.yml /usr/share/metasploit-framework/config/database.yml

WORKDIR /root
