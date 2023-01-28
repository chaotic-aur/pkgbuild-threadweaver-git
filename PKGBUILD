# Merged with official ABS threadweaver PKGBUILD by João, 2021/02/21 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=threadweaver-git
pkgver=5.80.0_r474.g737ace5
pkgrel=1
pkgdesc='High-level multithreading framework'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(qt5-base)
makedepends=(git extra-cmake-modules-git doxygen qt5-tools qt5-doc)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
      cd ${pkgname%-git}
        _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
          echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
      cmake -B build -S ${pkgname%-git} \
          -DBUILD_TESTING=OFF \
              -DBUILD_QCH=ON
                cmake --build build
}

package() {
      DESTDIR="$pkgdir" cmake --install build
}
source=("git+https://github.com/KDE/${pkgname%-git}#branch=kf5")
