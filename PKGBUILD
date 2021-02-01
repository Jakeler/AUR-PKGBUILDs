# Maintainer: courk <courk at courk dot fr>
pkgname=kaitai-struct-compiler
pkgver=0.9
pkgrel=1
pkgdesc="Kaitai Struct Compiler: Compiler for the Kaitai declarative binary format parsing language"
arch=(any)
url="http://kaitai.io/"
license=('GPL3')
depends=("java-runtime")
optdepends=()
source=("$pkgname-$pkgver.zip::https://bintray.com/kaitai-io/universal/download_file?file_path=$pkgver%2F$pkgname-$pkgver.zip"
        "01-fix_lib_dir.patch")
sha256sums=('3038243334fb65bbb264f33b82986facfe1fbad2de1978766899855b40212215'
            '11a49eae3903511c83fd43759d21ac4f430024fe7b6dba5d4ebef6f0ba3f05c6')

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
