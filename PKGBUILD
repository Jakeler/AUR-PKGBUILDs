# Maintainer: Thomas Krug <t.krug@elektronenpumpe.de>
# Contributor: Thomas Krug <t.krug@elektronenpumpe.de>
# Maintainer: Cody Schafer <aur@codyps.com>

pkgname=dsview
pkgver=1.01
pkgrel=1
pkgdesc="Client software that supports the DreamSourceLab logic analyzer"
arch=('i686' 'x86_64')
url="http://www.dreamsourcelab.com/"
license=('GPL3')
depends=('boost-libs' 'qt5-base' "libsigrokdecode4dsl=${pkgver}" "libsigrok4dsl=${pkgver}" 'fftw')
makedepends=('boost')

source=(
  "DSView-$pkgver.tar.gz::https://github.com/DreamSourceLab/DSView/archive/v${pkgver}.tar.gz"
  'udev.rules'
  'dsview.desktop'
  '0001-workaround-configure-failure-due-to-boost-cmake.patch'
)
sha384sums=('b8bf646f8c599cb8adfa2ab1363f36592a1ecb10b819617cecc970ac7a30b8d5ef912e9af5c1d55a9282478d8a55b80e'
            'cb8d28e4f0e20d81bccb7f81d3c2df9df13e13a45556bce9cbf0303f12d23564271bcc6afacf6a2801114dec50000729'
            '832521f6e13705d7abc99a94ab2a6cb8e1d8087444cdc283b9adc9ec2011da9a16242994af2ba6f339c7e455ba5df4ad'
            '338763e008464bebb1f11e62d3a4839d7af43c800f772be6d51a345f6e1e83fa4d5929c1e4b363dd9af2073dda420821')

_wdir() {
  cd "$srcdir/DSView-$pkgver/DSView"
}

prepare() {
  cd "$srcdir/DSView-$pkgver"
  patch -Np1 -i "$srcdir"/'0001-workaround-configure-failure-due-to-boost-cmake.patch'
  cd DSView
  sed -i 's#install(FILES icons/logo.png DESTINATION share/${PROJECT_NAME} RENAME logo.png)##;
          s#install(FILES DreamSourceLab.rules DESTINATION /etc/udev/rules.d/)##' \
    CMakeLists.txt
  cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_SKIP_RPATH=1 .
}

build() {
  _wdir
  cmake .
  make
}

package() {
  _wdir

  make DESTDIR="$pkgdir" PREFIX=/usr install

  install -Dm644 "$srcdir/dsview.desktop" "$pkgdir/usr/share/applications/dsview.desktop"
  install -Dm644 "$srcdir/udev.rules" "$pkgdir/usr/lib/udev/rules.d/20-dsview.rules"

  install -Dm644 icons/logo.png "${pkgdir}/usr/share/icons/hicolor/256x256/apps/${pkgname}.png"
}

# vim:set ts=2 sw=2 et:
