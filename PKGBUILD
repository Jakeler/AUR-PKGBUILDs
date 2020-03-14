# Maintainer: Cody Schafer <aur@codyps.com>
# Maintainer: Jake <aur@ja-ke.tech>
# Contributor: Thomas Krug <t.krug@elektronenpumpe.de>

pkgname=dsview
pkgver=1.10
pkgrel=1
pkgdesc="Client software that supports the DreamSourceLab logic analyzer"
arch=('i686' 'x86_64')
url="http://www.dreamsourcelab.com/"
license=('GPL3')
depends=('boost-libs' 'qt5-base' "libsigrokdecode4dsl>=${pkgver}" "libsigrok4dsl>=${pkgver}" 'fftw')
makedepends=('boost')

source=(
  "DSView-$pkgver.tar.gz::https://github.com/DreamSourceLab/DSView/archive/v${pkgver}.tar.gz"
  'udev.rules'
  'dsview.desktop'
)
sha384sums=('6cd82ee9c729db48f86aa00c492eb7e18a8b444d3bd7a384fbd7433e24758d7190ef88082457111b752d28c28145d9a5'
            '4f7c463e0723e3cfd6ed146e0db6b44627065af077aaca9765b60c9347752e32032752f04883da89b9f65523ca5c28e8'
            '6c47f8b81858cfccc96a0e18dd56dbb23c72baa165650d145898eea8d8f3493a9179f7c8c9afd651ed99e713c9106238')

_wdir() {
  cd "$srcdir/DSView-$pkgver/DSView"
}

prepare() {
  cd "$srcdir/DSView-$pkgver"
  
  cd DSView
  sed -i 's#install(FILES icons/logo.png DESTINATION share/${PROJECT_NAME} RENAME logo.png)##; 
          s#install(FILES DreamSourceLab.rules DESTINATION /etc/udev/rules.d/)##; 
          s#install(FILES DSView.desktop DESTINATION /usr/share/applications/)##' CMakeLists.txt
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
