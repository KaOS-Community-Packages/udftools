pkgname=udftools
pkgver=1.3
pkgrel=1
pkgdesc="Linux UDF tools"
url="https://github.com/pali/udftools"
license=('GPL')
depends=('ncurses' 'readline')
arch=('x86_64')
source=('udftools.tar.gz::https://github.com/pali/udftools/archive/1.3.tar.gz')
md5sums=('2958b1e2040d20147bb615edf11e007c')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./autogen.sh
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr --mandir=/usr/share/man
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
