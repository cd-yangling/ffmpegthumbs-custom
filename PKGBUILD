# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=ffmpegthumbs
pkgver=16.12.3
pkgrel=1
pkgdesc='FFmpeg-based thumbnail creator for video files'
url='https://www.kde.org/applications/multimedia/'
arch=(i686 x86_64)
license=(GPL LGPL FDL)
groups=(kde-applications kdemultimedia)
depends=(kio ffmpeg)
makedepends=(extra-cmake-modules)
replaces=(kdemultimedia-ffmpegthumbs)
source=("https://download.kde.org/stable/applications/$pkgver/src/$pkgname-$pkgver.tar.xz"{,.sig})
sha256sums=('09ff1e7b95fc34bd66bc8dc437c0a1562835f83dbb33f8c6ce41e85c50f39ee9'
            'SKIP')
validpgpkeys=(CA262C6C83DE4D2FB28A332A3A6A4DB839EAA6D7) # Albert Astals Cid <aacid@kde.org>

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
