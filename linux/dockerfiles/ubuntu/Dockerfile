FROM ubuntu:latest

# 非対話型のインストールプロセスを指定
# tzdata のインストール時に地域を指定させられる事を避ける
ENV DEBIAN_FRONTEND noninteractive

# パッケージ更新および新規インストール
RUN apt-get update && \
    apt-get -y install \
    sudo \
    build-essential \
    git \
    vim \
    tzdata

# Timezone の変更
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# ユーザ作成
ARG USER_NAME="shimajiro"
RUN useradd -m ${USER_NAME}
RUN echo "${USER_NAME}:${USER_NAME}" | chpasswd

# sudo の許可
RUN gpasswd -a ${USER_NAME} sudo
RUN echo "Set disable_coredump false" >> /etc/sudo.conf

# alias
RUN touch /home/${USER_NAME}/.bash_aliases
RUN chown ${USER_NAME}:${USER_NAME} /home/${USER_NAME}/.bash_aliases
RUN echo 'alias ..="cd .."'  >> /home/shimajiro/.bash_aliases
RUN echo 'alias ll="ls -l"'  >> /home/shimajiro/.bash_aliases
RUN echo 'alias la="ls -la"' >> /home/shimajiro/.bash_aliases

# PS1
RUN echo '\nPS1="[\u@myubuntu \W]\$ "' >> /home/${USER_NAME}/.bashrc

# vimrc
COPY ./settings/vimrc /home/${USER_NAME}/.vimrc
RUN chown ${USER_NAME}:${USER_NAME} /home/${USER_NAME}/.vimrc

WORKDIR /home/${USER_NAME}
CMD ["/bin/bash"]
