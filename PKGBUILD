# Contributor: Marius Dransfeld <marius.dransfeld@googlemail.com>
pkgname=libqtbamf-bzr
pkgver=398
pkgrel=1
pkgdesc="Qt bindings for libbamf"
arch=('i686' 'x86_64')
url="https://launchpad.net/bamf-qt"
license=('GPL')
depends=('qt4' 'bamf')
makedepends=('cmake' 'bzr')
conflicts=('libqtbamf')
replaces=('libqtbamf')
groups=('unity2d-bzr')

_bzrtrunk=lp:bamf-qt
_bzrmod=bamf-qt

build() {
  cd "$srcdir"
  
  if [ -d ${_bzrmod} ]; then
    bzr up ${_bzrmod}
    msg "The local files are updated."
  else
    bzr co ${_bzrtrunk} ${_bzrmod}
  fi
  if [[ -d ${srcdir}/build ]]; then
    msg "Cleaning the previous build directory..."
    rm -rf ${srcdir}/build 
  fi
  mkdir $srcdir/build
  cd $srcdir/build
  cmake $srcdir/$_bzrmod -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() { 
  cd ${srcdir}/build
  make DESTDIR="${pkgdir}" install
}
