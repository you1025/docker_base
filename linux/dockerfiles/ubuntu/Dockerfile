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
RUN useradd -m shimajiro
RUN echo "shimajiro:shimajiro" | chpasswd

# sudo の許可
RUN gpasswd -a shimajiro sudo
RUN echo "Set disable_coredump false" >> /etc/sudo.conf

# alias
RUN touch /home/shimajiro/.bash_aliases
RUN chown shimajiro:shimajiro /home/shimajiro/.bash_aliases
RUN echo 'alias ..="cd .."'  >> /home/shimajiro/.bash_aliases
RUN echo 'alias ll="ls -l"'  >> /home/shimajiro/.bash_aliases
RUN echo 'alias la="ls -la"' >> /home/shimajiro/.bash_aliases

# PS1
RUN echo '\nPS1="[\u@myubuntu \W]\$ "' >> /home/shimajiro/.bashrc

# vimrc
COPY ./settings/vimrc /home/shimajiro/.vimrc
RUN chown shimajiro:shimajiro /home/shimajiro/.vimrc

WORKDIR /home/shimajiro
CMD ["/bin/bash"]
