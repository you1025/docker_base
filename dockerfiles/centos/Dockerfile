FROM centos:latest

# パッケージ更新および新規インストール
RUN yum -y update && \
    yum -y install \
    sudo \
    vim \
    git

# ユーザ作成
RUN useradd -m shimajiro
RUN echo "shimajiro:shimajiro" | chpasswd

# sudo の許可
RUN usermod -aG wheel shimajiro

# alias
RUN echo 'alias vi=vim'          >> /home/shimajiro/.bashrc
RUN echo 'alias ..="cd .."'      >> /home/shimajiro/.bashrc
RUN echo 'alias ls="ls --color"' >> /home/shimajiro/.bashrc
RUN echo 'alias ll="ls -l"'      >> /home/shimajiro/.bashrc
RUN echo 'alias la="ls -la"'     >> /home/shimajiro/.bashrc

# PS1
RUN echo -e '\nPS1="[\u@mycentos \W]\$ "' >> /home/shimajiro/.bashrc

# vimrc
COPY ./settings/vimrc /home/shimajiro/.vimrc
RUN chown shimajiro:shimajiro /home/shimajiro/.vimrc

WORKDIR /home/shimajiro
CMD ["/bin/bash"]
