# Merged with official ABS kguiaddons PKGBUILD by João, 2021/02/01 (all respective contributors apply herein)
# Maintainer: João Figueiredo & chaotic-aur <islandc0der@chaotic.cx>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kguiaddons-git
_pkgname=kguiaddons
pkgver=v5.102.0.r15.g0aa7ca5
pkgrel=1
pkgdesc='Addons to QtGui'
arch=($CARCH)
url='https://invent.kde.org/frameworks/kguiaddons'
license=(LGPL)
depends=(qt6-wayland plasma-wayland-protocols)
makedepends=(git extra-cmake-modules-git clang python-pyqt6 doxygen qt6-tools sip4)
conflicts=(${_pkgname})
provides=(${_pkgname})
optdepends=('python-pyqt6: for the Python bindings')
groups=(kf6-git)
source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  git describe --long --abbrev=7 | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cmake -B build -S ${_pkgname} \
    -DQT_MAJOR_VERSION=6 \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
