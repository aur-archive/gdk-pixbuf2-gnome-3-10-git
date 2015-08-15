# Maintainer: Yosef Or Boczko <yosefor3@walla.com>

_pkgname=gdk-pixbuf2-gnome-3-10
pkgname=$_pkgname-git
pkgver=2.29.0.18.g27e6ad7
pkgrel=1
_realver=2.29.1
pkgdesc="An image loading library"
arch=('i686' 'x86_64')
url="http://www.gtk.org/"
license=('LGPL2.1')
depends=('glib2-gnome-3-10>=2.37.0' 'libpng' 'libtiff' 'libjpeg' 'libx11')
makedepends=('git' 'gtk-doc' 'gobject-introspection')
options=('!libtool')
install=gdk-pixbuf2.install
replaces=('gdk-pixbuf2')
provides=('gdk-pixbuf2' "gdk-pixbuf2=$_realver" "$_pkgname=$_realver")
conflicts=('gdk-pixbuf2')
source=(git://git.gnome.org/gdk-pixbuf)
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/gdk-pixbuf"
  git describe --always | sed 's|-|.|g'
}

build() {
  cd "$srcdir/gdk-pixbuf"

  ./autogen.sh --prefix=/usr \
    --without-libjasper \
    --with-x11 \
    --with-included-loaders=png \
    --enable-gtk-doc
  make
}

package() {
  cd "$srcdir/gdk-pixbuf"
  make DESTDIR="$pkgdir" install
}
