FROM base/archlinux:latest
MAINTAINER local

RUN sed 's/^CheckSpace/#CheckSpace/g' -i /etc/pacman.conf \
  && echo 'Server = http://lug.mtu.edu/archlinux/$repo/os/$arch' > /etc/pacman.d/mirrorlist \
  && pacman -Sy --quiet --noprogressbar --noconfirm archlinux-keyring \
  && pacman -Scc \
  && pacman-key --init \
  && pacman-key --populate archlinux \
  && pacman-key --refresh-keys \
  && pacman -Syyu --quiet --noprogressbar --noconfirm base-devel git yajl \
  && pacman-db-upgrade \
  \
  && cd /tmp/ \
  && git clone https://aur.archlinux.org/package-query \
  && chown -R nobody:nobody package-query \
  && cd package-query \
  && sudo -u nobody makepkg --noconfirm \
  && sudo pacman -U --noconfirm package-query*.pkg.tar.xz \
  \
  && cd /tmp/ \
  && git clone https://aur.archlinux.org/yaourt \
  && chown -R nobody:nobody yaourt \
  && cd yaourt \
  && sudo -u nobody makepkg --noconfirm \
  && sudo pacman -U --noconfirm yaourt*.pkg.tar.xz \
  \
  && useradd --create-home arch \
  \
  && useradd --create-home installer \
  && echo "installer ALL=(ALL) NOPASSWD: /usr/bin/pacman,/usr/bin/yaourt" >> /etc/sudoers \
  && echo -e "NOCONFIRM=1\nBUILD_NOCONFIRM=1\nEDITFILES=0" > ~installer/.yaourtrc \
  && chown -R installer:installer ~installer

ARG BUST_CACHE=0
RUN pacman -Syu --quiet --noprogressbar --noconfirm
