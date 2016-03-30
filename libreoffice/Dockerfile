FROM local/archlinux:latest
MAINTAINER local

RUN pacman -Syu --quiet --noprogressbar --noconfirm gtk2 jre8-openjdk libreoffice-still

USER arch
WORKDIR /home/arch
ENTRYPOINT [ "libreoffice" ]
