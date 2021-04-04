# Maintainer: Jake <aur@ja-ke.tech>
# Contributor: Alexander Scharinger
# Contributor: Tristan Webb <t2webb@ucsd.edu>
# Contributor Sindwiller

pkgname=pyspread
pkgver=1.99.6
pkgrel=1
pkgdesc="Python based non-traditional spreadsheet application"
arch=('any')
url="https://pyspread.gitlab.io/"
license=('GPL3')
depends=('python-setuptools'
        'python-dateutil'
        'python-numpy>=1.1.0'
        'python-pyqt5'
        'qt5-svg')
optdepends=('python-matplotlib'
            'python-pyenchant'
            'python-pip')
options=(!emptydirs)
source=("https://gitlab.com/pyspread/pyspread/-/archive/v${pkgver}/pyspread-v${pkgver}.tar.gz")
sha512sums=('e569ff2de5fcc3ecf0cb20c20c815093f5eaab05e0db2b7509aeb3d8a7ea982237c6ca7d0004a372d829e444a50e1fcee250cd5fdeb6d03995a2b7ca6fb75a8f')

package() {  
  cd "${srcdir}/${pkgname}-v${pkgver}"
  python setup.py install --root=$pkgdir/ --optimize=1

  install -D "${pkgname}/share/icons/$pkgname.svg" "$pkgdir/usr/share/pixmaps/$pkgname.svg"
  install -D -m644 "$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
}

