# Maintainer: Det <nimetonmaili at gmail a-dot com>
# Contributor: Alexander Rødseth <rodseth@gmail.com>
# Contributor: Giuseppe Borzi <gborzi@ieee.org>
# Based on mozplugger: https://aur.archlinux.org/packages/mozplugger/

pkgname=mozplugger-chromium
pkgver=2.1.6
pkgrel=1
pkgdesc="Mozilla multimedia plugin for Chromium"
arch=('x86_64' 'i686')
url='http://mozplugger.mozdev.org/'
license=('GPL')
depends=('libx11')
conflicts=('mozplugger')
backup=('etc/mozpluggerrc')
#source=("$url/files/mozplugger-$pkgver.tar.gz")
source=("http://ftp.osuosl.org/pub/mozdev/mozplugger/mozplugger-$pkgver.tar.gz")
md5sums=('abb42f3c3c2f3a940c1252a83f254116')

build() {
  cd mozplugger-$pkgver

  msg2 "Starting ./configure.."
  ./configure --prefix=/usr \
              --enable-always-xembed

  msg2 "Starting make.."
  make
}

package() {
  cd mozplugger-$pkgver

  msg2 "Putting stuff in place.."
  # Binaries
  install -d "$pkgdir"/usr/bin/
  install -m755 mozplugger-{helper,controller,linker,update} "$pkgdir"/usr/bin/

  # Plugin
  install -Dm755 mozplugger.so "$pkgdir"/usr/lib/mozilla/plugins/mozplugger.so

  # Config
  install -Dm644 mozpluggerrc "$pkgdir"/etc/mozpluggerrc

  # Man page
  gzip mozplugger.7
  install -Dm644 mozplugger.7.gz "$pkgdir"/usr/share/man/man7/mozplugger.7.gz
}
