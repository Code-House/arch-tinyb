# Maintainer: Łukasz Dywicki
pkgname=tinyb-git
_pkgname=tinyb
pkgver=0.5.1.r0.gac6d308
pkgrel=1
epoch=1
pkgdesc="Intel tinyb, a bluetooth LE api."

url="https://github.com/intel-iot-devkit/tinyb"
arch=('i686' 'x86_64')
license=('MIT')
depends=('bluez')
makedepends=(cmake git)

source=("$pkgname::git+https://github.com/intel-iot-devkit/$_pkgname.git")
md5sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --tags --long|sed -r 's,^[^0-9],,;s,([0-9]*-g),r\1,;s,[-_],.,g'
}

prepare() {
  mkdir "$pkgname/build"
}

build() {
  cd "$pkgname/build"
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR='/usr/lib' \
    -DCMAKE_SKIP_RPATH='TRUE' \
    -DBUILDJAVA=ON \
    ..
  make
}
  
package() {
  echo "${pkgdir}"

  cd "$pkgname/build"
  make DESTDIR="${pkgdir}" install

}
