from ubuntu:22:04

ARG DEBIAN_FRONTEND=noninteractive

ENV TZ Asia/Seoul
ENV PYTHONIOENCODING UTF-8
ENV LC_CTYPE C.UTF-8

WORKDIR /root

RUN export LC_CTYPE=C.UTF-8
RUN apt update && apt install -y netcat
RUN apt install vim git gcc ssh curl wget gdb sudo zsh python3 python3-pip libffi-dev build-essential libssl-dev libc6-i386 libc6-dbg gcc-multilib make -y

RUN dpkg --add-architecture i386
RUN apt update
RUN apt install libc6:i386 -y

RUN python3 -m pip install --upgrade pip
RUN pip3 install unicorn keystone-engine pwntools ropgadget
RUN apt install libcapstone-dev -y

RUN apt install ruby-full -y
RUN gem install one_gadget seccomp-tools

RUN wget http://howdays.kr/public/gdb/Pwngdb.zip
RUN unzip Pwngdb.zip
RUN rm Pwngdb.zip
RUN wget -O gdbinit http://howdays.kr/public/gdb/gdbinit
RUN mv $HOME/gdbinit $HOME/.gdbinit
RUN git clone https://github.com/pwndbg/pwndbg.git
RUN cd pwndbg && ./setup.sh

RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN mkdir -p "$HOME/.zsh"

RUN git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
RUN echo "source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
RUN echo "ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=111'" >> ~/.zshrc