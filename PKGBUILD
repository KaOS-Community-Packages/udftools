pkgname=udftools
pkgver=1.0.0b3
pkgrel=1
pkgdesc="Linux UDF tools"
url="http://sourceforge.net/projects/linux-udf/"
license=(GPL)
depends=('ncurses' 'readline')
arch=('x86_64')
source=("http://downloads.sourceforge.net/sourceforge/linux-udf/$pkgname-$pkgver.tar.gz"
        'udftools-1.0.0b3.patch.bz2'
        'gcc4-compile.patch.bz2'
        'udftools-limits.patch.bz2'
        'udftools-open_missing_mode.patch'
        'gcc5-compile-fix.patch')
options=(!libtool)
md5sums=('2f491ddd63f31040797236fe18db9e60'
         '5c760ad80d05ca19a88c6c4f503abc6f'
         '494ddf016b05c65c049406359b3238bf'
         '7f037d997f9e22eba2ecd07ffae4d203'
         'ff606c797dbfc04a07781b5cadf2cb6d'
         '629392c8268752855fe2dbd91295dcbf')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  # pktsetup patch from LFS
  patch -p1 -i "$srcdir/udftools-1.0.0b3.patch"

  # this fixes gcc4 compilation, but don't blame me if it doesn't work
  patch -p1 -i "$srcdir/gcc4-compile.patch"
  patch -p1 -i "$srcdir/udftools-limits.patch"
  
  # https://bugs.gentoo.org/show_bug.cgi?id=232100
  patch -p0 -i "$srcdir/udftools-open_missing_mode.patch"

  # fix for gcc5 compilation
  patch -p0 -i "$srcdir/gcc5-compile-fix.patch"
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --mandir=/usr/share/man
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make -C "$srcdir/$pkgname-$pkgver" DESTDIR="$pkgdir" install
}

