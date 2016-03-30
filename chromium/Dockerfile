FROM local/archlinux:latest
MAINTAINER local

RUN pacman -Syu --quiet --noprogressbar --noconfirm chromium

USER arch
WORKDIR /home/arch
ENTRYPOINT  [ "chromium" ]
