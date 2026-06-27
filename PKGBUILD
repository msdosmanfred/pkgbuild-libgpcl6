# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Alexander Höfer <hoefer9(AT)gmail.com>
pkgname=libgpcl6
_pkgname=ghostpdl
pkgver=10.07.1
pkgrel=1
#cdepoch=1
pkgdesc="GhostPCL library for use with 86Box's PCL printing feature"
arch=('x86_64')
url="https://www.ghostscript.com/"
license=('AGPL-3.0-or-later')
depends=('freetype2' 'libxft' 'ghostscript')
makedepends=('base-devel')
provides=('libgpcl6')
conflicts=('libgpcl6-git')
source=(https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs${pkgver//./}/ghostpdl-${pkgver}.tar.gz)
sha256sums=('5c580ed888ce42ce4d76b8afac302e8b507e08d05e52e05b3649e0732559bfe4')

prepare() {
  cd $srcdir/$_pkgname-$pkgver
  ./autogen.sh --prefix=/usr --without-xps
}

build() {
  cd $srcdir/$_pkgname-$pkgver
  make so-only
}

package() {
  cd $srcdir/$_pkgname-$pkgver
  make DESTDIR="$pkgdir/" install-so-gpcl6
  rm -f $pkgdir/usr/include/ghostscript/gdevdsp.h
  rm -f $pkgdir/usr/include/ghostscript/gserrors.h
}
