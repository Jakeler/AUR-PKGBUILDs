# Maintainer: Alexander Scharinger <e1028732 at student dot tuwien dot ac dot at>
# Contributor: Tristan Webb <t2webb@ucsd.edu>
# Contributor Sindwiller
pkgname=pyspread
pkgver=1.0.2
pkgrel=1
pkgdesc="A cross-platform Python spreadsheet application. Python 2.7 version"
arch=('any')
url="https://manns.github.io/pyspread/"
license=('GPL3')
depends=('python2>=2.7.0' 'python2-numpy>=1.1.0' 'wxpython' 'python2-matplotlib'
         'cairo>=1.8.8')
options=(!emptydirs)
source=('https://pypi.python.org/packages/source/p/pyspread/pyspread-1.0.2.tar.gz')
# The pyspread website lists another optional dependency: pyrsvg>=2.32, for
# displaying SVG files in cells. I believe pyrsvg is included in cairo (from
# the mandatory dependencies).
# See: https://manns.github.io/pyspread/download.html and on this site follow
# link to pyrsvg.
optdepends=('python2-gnupginterface: for opening files without approval' # in AUR
            'python2-xlrd: open Excel files' # in Community
            'python2-xlwt: save Excel files' # in Community
            'python2-jedi: TAB autocompletion and context help in the entry line' # in Community
            'python2-basemap: for the weather example' ) # in Community
md5sums=('0257adf5b5145c40808b40cca636af48')

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  python2 setup.py install --root=$pkgdir/ --optimize=1
  mv $pkgdir/usr/lib/python2.7/site-packages/{changelog,README} \
     $pkgdir/usr/lib/python2.7/site-packages/pyspread/
}

# vim:set ts=2 sw=2 et:
