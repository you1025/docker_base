FROM ubuntu:latest

# パッケージ更新および新規インストール
RUN apt-get update && \
    apt-get -y install \
    sudo \
    git \
    vim \
    build-essential

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
RUN echo -e '\nPS1="[\u@myubuntu \W]\$ "' >> /home/shimajiro/.bashrc

# vimrc
COPY ./settings/vimrc /home/shimajiro/.vimrc
RUN chown shimajiro:shimajiro /home/shimajiro/.vimrc

CMD ["/bin/bash"]
