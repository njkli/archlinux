# njkli archlinux repo
  Because, why pollute AUR?

## Installation

```
# install the keyring
baseurl='https://github.com/njkli/archlinux/releases/download/keyring'
kring="$baseurl/njkli-keyring-20170902-1-any.pkg.tar.xz"
kring_sig="$baseurl/njkli-keyring-20170902-1-any.pkg.tar.xz.sig"
kring_files=($kring $kring_sig)

for i in $kring_files; do curl -OfssL $i; done

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
