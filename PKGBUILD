# Maintainer: courk <courk at courk dot fr>
pkgname=kaitai-struct-compiler
pkgver=0.5
pkgrel=2
pkgdesc="Kaitai Struct Compiler: Compiler for the Kaitai declarative binary format parsing language"
arch=(any)
url="http://kaitai.io/"
license=('GPL3')
depends=("java-runtime")
optdepends=()
source=("$pkgname-$pkgver.zip::https://bintray.com/kaitai-io/universal/download_file?file_path=$pkgver%2F$pkgname-$pkgver.zip" "01-fix_lib_dir.patch")
sha1sums=("2df2f889233df6856ed98f0ab453bafe8c736512"
          "48c0e5d2682c61d4cea023d19882eb92c191cc1a")

prepare() {
  cd $pkgname-$pkgver
  patch -Np1 -i "${srcdir}/01-fix_lib_dir.patch"
}

package() {
  cd "$srcdir/$pkgname-$pkgver/lib/"
  for f in *.jar
  do
    install -D -m 644 "$f" "$pkgdir/usr/share/java/$pkgname/$f"
  done
  install -D -m 755 "$srcdir/$pkgname-$pkgver/bin/kaitai-struct-compiler" "$pkgdir/usr/bin/kaitai-struct-compiler"
}

# vim:set ts=2 sw=2 et:
