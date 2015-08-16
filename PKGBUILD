# Contributor: Rainy <rainylau(at)gmail(dot)com>
# Contributor: Lee.MaRS <leemars at gmail dot com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Maintainer : Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=ibus-wout-gconf
_pkgname=ibus
pkgver=1.4.2
pkgrel=1
pkgdesc='Next Generation Input Bus for Linux. WITHOUT GCONF'
arch=('i686' 'x86_64')
license=('LGPL')
url='http://ibus.googlecode.com'
depends=('python2-dbus' 'python2-xdg' 'iso-codes' 'librsvg' 'python2-notify' 'hicolor-icon-theme')
provides=('ibus')
conflicts=('ibus')
optdepends=('notification-daemon')
makedepends=('intltool' 'gobject-introspection')
options=('!libtool')
install=ibus.install
source=(http://ibus.googlecode.com/files/${_pkgname}-${pkgver}.tar.gz)
sha1sums=('a2d11d8bb64761691df918e9e50f0b35c711760d')

build() {
  rm -fr ${_pkgname}-${pkgver}-build
  cp -R ${_pkgname}-${pkgver} ${_pkgname}-${pkgver}-build
  cd ${_pkgname}-${pkgver}-build

  # python2 fix
  export PYTHON=python2

  sed -i 's|--pkg=ibus-1.0||' src/Makefile.in
  ./configure --prefix=/usr --libexecdir=/usr/lib/ibus --sysconfdir=/etc --disable-gconf --disable-schemas-install --enable-gtk3
  make
}

package() {
  cd ${_pkgname}-${pkgver}-build
  make DESTDIR="${pkgdir}" install
  install -d "${pkgdir}"/etc/xdg/autostart
  ln -s /usr/share/applications/ibus.desktop "${pkgdir}"/etc/xdg/autostart/ibus.desktop
}
