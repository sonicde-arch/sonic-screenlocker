# Maintainer: artist for Sonic-DE

pkgname=sonic-screenlocker
pkgver=6.6.5.2
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
source=("$pkgname-$pkgver.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
        kde.pam
        kde-fingerprint.pam
        kde-smartcard.pam)

build() {
  cmake -B build  -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  install -Dm644 "$srcdir"/kde.pam "$pkgdir"/usr/lib/pam.d/kde
  install -Dm644 "$srcdir"/kde-fingerprint.pam "$pkgdir"/usr/lib/pam.d/kde-fingerprint
  install -Dm644 "$srcdir"/kde-smartcard.pam "$pkgdir"/usr/lib/pam.d/kde-smartcard
}

sha256sums=('a27ee17ab7e5469d9f75625cd194f739f645f235771092c0acd377e4bf8c3d76')
