FROM ubuntu:16.04

MAINTAINER Laurent Aphecetche <laurent.aphecetche@gmail.com>

RUN apt-get update && \
apt-get install -y software-properties-common && \
add-apt-repository -y ppa:neovim-ppa/unstable && \
apt-get update && \
apt-get install -y neovim python-dev python-pip git

RUN pip install neovim

RUN git clone --depth=1 https://github.com/aphecetche/dotfiles.git && \
 mkdir /root/.config && \
 mv dotfiles/config/nvim /root/.config/ && \
 ln -s /root/.config/nvim /root/.vim && \
 ln -s /root/.config/nvim/init.vim /root/.vimrc

ADD vimrc /root/.config/nvim/init.vim
ADD bashrc /root/.bashrc

RUN nvim --headless -c "PlugInstall! | qall! " 

ENV BACKGROUND=light
ENV THEME=base16-solarized

ENTRYPOINT /usr/bin/nvim

