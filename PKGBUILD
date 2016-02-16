# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=ffmpegthumbs
pkgver=15.12.2
pkgrel=2
pkgdesc='FFmpeg-based thumbnail creator for video files'
url='https://projects.kde.org/ffmpegthumbs'
arch=(i686 x86_64)
license=(GPL LGPL FDL)
groups=(kde-applications kdemultimedia)
depends=(kio ffmpeg)
makedepends=(extra-cmake-modules git)
replaces=(kdemultimedia-ffmpegthumbs)
source=("http://download.kde.org/stable/applications/$pkgver/src/$pkgname-$pkgver.tar.xz"
	ffmpegthumbs-ffmpeg3.patch::"https://git.reviewboard.kde.org/r/126992/diff/raw/")
md5sums=('3e56e870a963fbc7e0c1b873628e56e7'
         '0e3a9b044e2d94be9c608ad6369e9c7f')

prepare() {
  mkdir -p build

  cd $pkgname-$pkgver
# Fix build against ffmpeg 3.0
  patch -p1 -i ../ffmpegthumbs-ffmpeg3.patch
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_TESTING=OFF \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
