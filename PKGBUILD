# Maintainer: Ner0

pkgname=marlin-bin
pkgver=LATEST
_pkgver=0.1.`curl -s http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/pool/main/m/marlin/ | \
grep -o marlin.*~oneiric.*deb | tail -1 | cut -d~ -f2`
pkgrel=1
arch=('i686' 'x86_64')
_arch=amd64
[ $CARCH = 'i686' ] && _arch=i386
pkgdesc="A sleek and fast GTK3 file manager (Ubuntu prebuilt)"
url="https://launchpad.net/marlin"
license=('GPL2' 'GPL3')
depends=('gtk3' 'libgee' 'glib2' 'cairo' 'libnotify' 'gnome-icon-theme' 'varka-bzr' 'libdbusmenu' 'dee' 'dconf')
makedepends=('lynx' 'wget' 'libarchive')
optdepends=('extended-actions-bzr: Plugins integration [AUR]'
            'egtk-bzr: Elementary GTK Theme [AUR]'
            'marlin-dropbox-plugin-bzr: Dropbox integration [AUR]')
conflicts=('marlin-bzr')
install=marlin-bin.install

FORCE_VER="$_pkgver"

build() {
  rm -rf * 2>/dev/null
  wget `lynx -dump http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/pool/main/m/marlin | \
	grep -o http.*oneiric.*$_arch.deb | tail -1`
  bsdtar -xf *.deb data.tar.xz
  bsdtar -xf data.tar.xz -C "$pkgdir/"
  if [ ! -f /usr/lib/libunity.so.[0-9] ]; then
    rm -rf * 2>/dev/null
    wget `lynx -dump http://archive.ubuntu.com/ubuntu/pool/main/libu/libunity/ | \
	grep -o http.*$_arch.deb | tail -1`
    bsdtar -xf libunity*.deb data.tar.*
    bsdtar -xf data.tar.*
    mv usr/lib/libunity* "$pkgdir/usr/lib"
  fi
}

# vim:set ts=4 sw=4 et:
