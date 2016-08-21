# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=ffmpegthumbs
pkgver=16.08.0
pkgrel=1
pkgdesc='FFmpeg-based thumbnail creator for video files'
url='https://www.kde.org/applications/multimedia/'
arch=(i686 x86_64)
license=(GPL LGPL FDL)
groups=(kde-applications kdemultimedia)
depends=(kio ffmpeg)
makedepends=(extra-cmake-modules git)
replaces=(kdemultimedia-ffmpegthumbs)
source=("http://download.kde.org/stable/applications/$pkgver/src/$pkgname-$pkgver.tar.xz")
md5sums=('fe4ab4ee08582ec8cdf4ade1b182b725')

prepare() {
  mkdir -p build
}

build() {
  cd build
  export PKG_CONFIG_PATH="/usr/lib/ffmpeg2.8/pkgconfig"
  cmake ../$pkgname-$pkgver \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_TESTING=OFF \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DKDE_INSTALL_LIBDIR=lib
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
