FROM base/archlinux:latest
LABEL maintainer="developers@moneymanagerex.org"
RUN pacman -Syuq --noprogressbar --needed --noconfirm \
      git cmake make gcc gettext fakeroot lsb-release \
      webkit2gtk wxgtk3 rapidjson && \
    pacman -Qdtq | xargs -r pacman -Rns --noconfirm && \
    pacman -Sc --noconfirm

# unlock nobody required for makepkg
RUN usermod nobody -s /usr/bin/bash

# fix broken wxgtk3
RUN ln -sf /usr/bin/wx-config{-gtk3,} || true

ENV MMEX_INST_CMD pacman -U --noconfirm ./mmex-*.pkg.tar.xz
