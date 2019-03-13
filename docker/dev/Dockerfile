FROM edvint-infer
RUN apt-get update -y && \
    apt-get install -y neovim python3-pip stow tig zsh clang && \
    apt-get clean && \
    (cd /infer && make devsetup && make && make toplevel)
RUN  echo 'deb http://deb.debian.org/debian stretch-backports main' >/etc/apt/sources.list.d/backports.list
RUN apt-get update && apt-get install -y neovim -t stretch-backports && apt-get clean
RUN git clone --depth 1 --recursive https://gitlab.com/edwintorok/dotfiles.git ~/dotfiles && \
    rm -rf ~/dotfiles/.git ~/dotfiles/emacs ~/dotfiles/fonts && \
    (cd ~/dotfiles && make install-nogui)
ENV LANG=C.UTF-8
ENTRYPOINT [ "/usr/bin/zsh", "-l" ]
