# Maintainer: Jake <ja.ke@posteo.de>

pkgname=hyperion.ng-git
pkgver=r1567.e438bc62
pkgrel=1
pkgdesc="The reworked version (next generation) of Hyperion, ambient light software - PRE ALPHA"
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/hyperion-project/hyperion.ng"
license=('MIT')
depends=('libusb' 'protobuf' 'python' 'qt5-serialport' 'avahi')
optdepends=('xorg-server: X11 grabbing')
makedepends=('cmake')
provides=("hyperion")
conflicts=('hyperion' 'hyperion-git')
backup=('etc/hyperion/config/hyperion.config.json')
source=("git+https://github.com/hyperion-project/${pkgname%-git}"
        "hyperion.systemd")
sha512sums=('SKIP'
            '18ce37552465c654e159062d5e104b43d5bc19a3f31b76293b294bef95f1998bfe357bc70c259f3c495c2e5d4abfb9c7e47a0b76c5bd89c69d294dd9d37de1ac')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${srcdir}/${pkgname%-git}"
  
  sed -i "s/python/python2/g" CMakeLists.txt
  
  mkdir build && cd build
  cmake -DCMAKE_BUILD_TYPE=Release \
        -DPROTOBUF_PROTOC_EXECUTABLE=/usr/bin/protoc \
        -DUSE_SYSTEM_PROTO_LIBS=ON \
        ..
  make
}

package() {
  cd "${srcdir}/${pkgname%-git}"
  
  install -d ${pkgdir}/usr/bin
  install -D build/bin/* ${pkgdir}/usr/bin
  
  install -d ${pkgdir}/usr/share/hyperion/webconfig
  cp -r assets/webconfig ${pkgdir}/usr/share/hyperion/  
  
  install -Dm 644 config/hyperion.config.json.default "${pkgdir}/etc/hyperion/config/hyperion.config.json"

  install -Dm 644 ${srcdir}/hyperion.systemd "${pkgdir}/usr/lib/systemd/system/hyperiond.service"

  install -Dm 644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname%-git}/LICENSE"
}
