# njkli archlinux repo
  Because, why pollute AUR?

## Installation

```
# install the keyring
kring='https://github.com/njkli/archlinux/releases/download/keyring/njkli-keyring-20170902-1-any.pkg.tar.xz'
kring_sig='https://github.com/njkli/archlinux/releases/download/keyring/njkli-keyring-20170902-1-any.pkg.tar.xz.sig'
keyring_files=($kring $kring_sig)

for i in $keyring_files; do curl -OfssL $i; done

gpg --keyserver hkp://keys.gnupg.net --recv-keys A09383D0550C42E2D6CE7C822F90CB4F042140DC
gpg --verify njkli-keyring-20170902-1-any.pkg.tar.xz.sig

sudo pacman -U njkli-keyring-20170902-1-any.pkg.tar.xz

sudo runuser -l -c \
'cat >> /etc/pacman.conf << EOL
[njkli]
SigLevel = Required DatabaseOptional TrustedOnly
Server = https://github.com/$repo/archlinux/releases/download/$arch
EOL
'

sudo pacman -Syyu
```

## Packages
  * anydesk
