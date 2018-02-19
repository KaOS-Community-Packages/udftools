pkgname=udftools
pkgver=2.0
pkgrel=1
pkgdesc="Linux UDF tools"
url="https://github.com/pali/${pkgname}"
license=('GPL')
depends=(
    'ffmpeg'
    'gcc'
    'glibc'
    'libcdio'
    'linux-api-headers'
    'ncurses'
    'pciutils'
    'readline'
)
makedepends=(
    'autoconf'
    'automake'
    'findutils'
    'libtool'
)
arch=('x86_64')
source=("${pkgname}.zip::${url}/archive/${pkgver}.zip")
md5sums=('6e930f0b35307586a93196826f51a7ba')

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
