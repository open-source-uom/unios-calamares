# Maintainer: Apostolos Chalis <achalis@csd.auth.gr>
pkgname=unios-calamares
pkgver=3.4.3
pkgrel=1
pkgdesc="Distribution-independent installer framework (UniOS fork)"
arch=('x86_64')
url="https://github.com/open-source-uom/unios-calamares"
license=('GPL3')

depends=(
    'boost-libs'
    'hwinfo'
    'kconfig'
    'kcoreaddons'
    'ki18n'
    'kpmcore'
    'kservice'
    'kwidgetsaddons'
    'libpwquality'
    'parted'
    'polkit-qt6'
    'python'
    'qt6-base'
    'qt6-declarative'
    'qt6-svg'
    'solid'
    'yaml-cpp'
)
makedepends=(
    'boost'
    'cmake'
    'extra-cmake-modules'
    'git'
    'ninja'
    'qt6-tools'
)

provides=('calamares')
conflicts=('calamares')

source=("git+https://github.com/open-source-uom/unios-calamares.git#branch=calamares")
sha256sums=('SKIP')

build() {
    cd "${srcdir}/unios-calamares"

    cmake -B build -G Ninja \
        -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_INSTALL_LIBDIR=lib \
        -DWITH_QT6=ON \
        -DBUILD_TESTING=OFF \
        -DINSTALL_CONFIG=ON

    cmake --build build
}

package() {
    cd "${srcdir}/unios-calamares"
    DESTDIR="${pkgdir}" cmake --install build
}