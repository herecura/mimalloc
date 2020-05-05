# Maintainer: René Wagner < rwagner at rw-net dot de >

pkgname=mimalloc
pkgver=1.6.3
pkgrel=1
pkgdesc='General-purpose allocator with excellent performance characteristics'
arch=('x86_64')
license=('MIT')
url='https://github.com/microsoft/mimalloc'
conflicts=('mimalloc-git')
depends=('glibc')
makedepends=('cmake' 'git')
provides=('mimalloc')
options=('staticlibs')
source=("${pkgname}::git+https://github.com/microsoft/${pkgname}.git#tag=v${pkgver}")
sha256sums=('SKIP')

build() {
  cd "${pkgname}"
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr .
  make
}

package() {
  cd "${pkgname}"
  make DESTDIR="${pkgdir}" install

  #ln -s "mimalloc-1.6/libmimalloc.so.1.6" "${pkgdir}/usr/lib/"
  (
    cd "${pkgdir}/usr/lib"
    find -iname "libmimalloc*so*" -exec ln -s {} \;
  )

  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
