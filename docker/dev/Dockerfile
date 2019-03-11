FROM edwintorok/infer
RUN apt-get update -y && \
    apt-get install -y neovim python3-pip stow tig zsh clang && \
    apt-get clean && \
    (cd /infer && make devsetup && make && make toplevel)
RUN git clone --depth 1 --recursive https://gitlab.com/edwintorok/dotfiles.git ~/dotfiles && \
    rm -rf ~/dotfiles/.git ~/dotfiles/emacs ~/dotfiles/fonts && \
    (cd ~/dotfiles && make install-nogui)
ENTRYPOINT [ "/usr/bin/zsh", "-l" ]
