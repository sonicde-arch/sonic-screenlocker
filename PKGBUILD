# Maintainer: artist for Sonic-DE

pkgname=sonic-screenlocker
pkgver=6.6.5
_dirver=$(echo $pkgver | cut -d. -f1-3)
pkgrel=1
pkgdesc='Library and components for Sonic-DE secure lock screen architecture'
arch=(x86_64)
url='https://github.com/Sonic-DE/sonic-screenlocker'
license=(LGPL-2.0-or-later)
depends=(gcc-libs
         glibc
         kconfig
         kcoreaddons
         kcrash
         kdeclarative
         ki18n
         kidletime
         kio
         kirigami
         knotifications
         kpackage
         ksvg
         kxmlgui
         libx11
         libxcb
         libxi
         pam
         qt6-base
         qt6-declarative
         sonic-frameworks-keybind
         sonic-frameworks-windowsystem
         sonic-interface-libraries
         sonic-screen-library
         xcb-util-keysyms)
makedepends=(extra-cmake-modules
             kcmutils
             kdoctools)
optdepends=('kcmutils: configuration module')
groups=(sonicde)
conflicts=(kscreenlocker)
provides=(kscreenlocker)
source=("$pkgname-$pkgver.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz")

build() {
  cmake -B build  -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

sha256sums=('8c188997f7f673012a3be842a4699ae5d56b3e4d2ade44337b97eb0a5cf885ad')
