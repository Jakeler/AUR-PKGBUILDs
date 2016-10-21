# Maintainer: Rinus Remspoor <remspoor AT linuxmail DOT org>

pkgname=next
pkgver=1.455
pkgrel=1
pkgdesc="CGM rc Heli Flight Simulator"
arch=('i686' 'x86_64')
url="http://www.rc-aerobatics.eu/index_e.html"
license=('custom')
groups=()
backup=()
options=()
install=
depends=()
optdepends=(	'joyutils: jscal, jstest, and jsattach utilities for the Linux joystick driver')

source=(	'http://www.cgm-online.com/secure_rc-heli-simulator/cgm-rc-heli-simulator-linux-x86-64bit.zip'
		'next.desktop'
		'next.LICENSE')

sha256sums=(	'9c07767316866e40099064d2ba053786e7420cdeab0cf87288c16bb3b0a0e102'
		'3acf4a84a47c281aa77c71004a28cc7be284854c98bb302da5e52002a3cc9afd'
		'febb1e65a7932f2f80155078b1dd64f469433625c76cff43b239768a184729f0')

prepare() {
  # rename the original directory to something sane and remove an OSX directory
  mv "Linux x86+64bit" "${pkgname}"
  rm -r "__MACOSX"

  cd "${srcdir}/${pkgname}"

  # Remove unneeded architecture/platform dependent files
  msg2 "Removing unneeded files..."
  find . -name '.DS_Store' -exec rm {} \;

  if [ "${CARCH}" == 'i686' ]; then
    rm -r ./neXt_Data/Mono/x86_64
    rm -r ./neXt_Data/Plugins/x86_64
    rm ./neXt.x86_64
  fi
  if [ "${CARCH}" == "x86_64" ]; then
    rm -r ./neXt_Data/Mono/x86
    rm -r ./neXt_Data/Plugins/x86
    rm ./neXt.x86
  fi
}

package() {
  # Install files to ${pkgdir}
  install -dm755 "${pkgdir}/opt/${pkgname}"

  msg2 "Copying files to package directory..."
  cp -dr --no-preserve=ownership "${srcdir}/${pkgname}" "${pkgdir}/opt/"

  msg2 "Installing icon file..."
  install -Dm644 "${srcdir}/${pkgname}/neXt_Data/Resources/UnityPlayer.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"

  msg2 "Installing ${pkgname}.desktop file..."
  install -Dm644 "${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"

  msg2 "Installing LICENSE file..."
  # Can't find the proper license right now, maybe contact the author of the software later.
  install -Dm644 ${pkgname}.LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  msg2 "Creating symlink..."
  cd "${pkgdir}/opt/${pkgname}"
  if [ -f "./neXt.x86_64" ]; then ln -s "neXt.x86_64" "${pkgname}"; fi
  if [ -f "./neXt.x86" ]; then ln -s "neXt.x86" "${pkgname}"; fi

}
