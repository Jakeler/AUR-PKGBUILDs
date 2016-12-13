#
# Maintainer: Guilhelm Savin <aur@gsav.in>
# Upstream URL: https://github.com/platformio/platformio
#
# For improvements/fixes to this package, please send a pull request:
# https://github.com/gsavin/arch
#

pkgname=platformio
pkgver=3.2.1
pkgrel=1
pkgdesc="A cross-platform code builder and library manager"
arch=('any')
url="https://github.com/platformio/platformio-core/"
license=('Apache')
depends=('python2'
         'python2-bottle'
         'python2-click-5.1' # https://github.com/platformio/platformio/issues/349
         'python2-colorama'
         'python2-lockfile'
         'python2-pyserial'
         'python2-requests'
         'python2-semantic-version'
         'python2-setuptools')
conflicts=('platformio-git')
source=("https://github.com/platformio/platformio-core/archive/v${pkgver}.tar.gz")
sha256sums=('5a85e60afc28b4ee04b43efd90c77f69b6c6ff96829e1b8750aa52143bca6eb2')

package() {
    cd "$srcdir/platformio-core-$pkgver"
    python2 setup.py install --root="$pkgdir/" --optimize=1
}
