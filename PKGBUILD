# Maintainer: Jake <ja.ke@posteo.de>
# Original Maintainer: jose <jose1711 [at] gmail (dot) com>
# Contributor: Roman Ajsin <aysin (dot) roman [at] gmail (dot) com>

pkgname=geekbench
pkgver=4.1.1
pkgrel=1
pkgdesc="A cross-platform benchmark that measures processor and memory performance"
arch=('i686' 'x86_64')
url="http://www.primatelabs.ca/geekbench/"
depends=('zlib' 'gcc-libs')
license=("custom")
conflicts=("geekbench227")
source=("http://cdn.primatelabs.com/Geekbench-${pkgver}-Linux.tar.gz")
md5sums=('9ef00bd21002f66041392a8c0b3f3607')
options=('!strip')

package() {
install -D -m755 $srcdir/build.pulse/dist/Geekbench-${pkgver}-Linux/${pkgname}_x86_32 $pkgdir/opt/${pkgname}/${pkgname}_x86_32
install -D -m755 $srcdir/build.pulse/dist/Geekbench-${pkgver}-Linux/${pkgname}_x86_64 $pkgdir/opt/${pkgname}/${pkgname}_x86_64
install -D -m755 $srcdir/build.pulse/dist/Geekbench-${pkgver}-Linux/${pkgname}4 $pkgdir/opt/${pkgname}/
install -D -m644 $srcdir/build.pulse/dist/Geekbench-${pkgver}-Linux/geekbench.plar $pkgdir/opt/${pkgname}/geekbench.plar
mkdir -p $pkgdir/usr/bin
ln -s /opt/${pkgname}/${pkgname}4 $pkgdir/usr/bin/${pkgname}
}
