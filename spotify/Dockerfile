FROM local/archlinux:latest
MAINTAINER local

RUN pacman -Syu --quiet --noprogressbar --noconfirm alsa-utils ttf-dejavu \
  && sudo -u installer yaourt -S spotify \
  && mkdir -p ~arch/.config/spotify ~arch/.cache/spotify \
  && chown -R arch:arch ~arch \
  && gpasswd -a arch audio

USER arch
WORKDIR /home/arch
ENTRYPOINT  [ "spotify" ]
