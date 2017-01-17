FROM ubuntu:16.04

MAINTAINER Laurent Aphecetche <laurent.aphecetche@gmail.com>

RUN apt-get update && \
apt-get install -y software-properties-common && \
add-apt-repository -y ppa:neovim-ppa/unstable && \
apt-get update && \
apt-get install -y neovim python-dev python-pip git cmake curl clang-format && \
pip install neovim

RUN cd $HOME && git clone --depth=1 https://github.com/aphecetche/dotfiles.git && \
 mkdir /root/.config && \
 mv $HOME/dotfiles/config/nvim /root/.config/ && \
 ln -s /root/.config/nvim /root/.vim && \
 ln -s /root/.config/nvim/init.vim /root/.vimrc && \
 git clone --depth=1 https://github.com/aphecetche/base16-shell.git /root/dotfiles/base16-shell && \
 nvim --headless -c "PlugInstall! | qall! " 

ADD vimrc /root/.config/nvim/init.vim
ADD bashrc /root/.bashrc

ENV BACKGROUND=light
ENV THEME=base16-solarized-light

# here should remove all what's no longer needed to _run_ neovim, but was used
# to build some of the plugins, e.g. cmake, git, curl, python-dev (?)

ENTRYPOINT /usr/bin/nvim

