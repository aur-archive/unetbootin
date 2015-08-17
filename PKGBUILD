# Maintainer: Det <nimetonmaili at gmail a-dot com>
# Contributor: Godane aka Christopher Rogers <slaxemulator@gmail.com>
pkgname=unetbootin
pkgver=555
pkgrel=1
pkgdesc="Lets you create bootable Live USB drives"
url="http://unetbootin.sourceforge.net/"
license=('GPL')
arch=('i686' 'x86_64')
depends=('syslinux' 'p7zip' 'qt' 'mtools' 'libpng')
optdepends=('gksu: for graphically requesting the root password'
            'kdebase-runtime: for graphically requesting the root password')
install=${pkgname}.install
source=(http://downloads.sourceforge.net/project/${pkgname}/UNetbootin/${pkgver}/${pkgname}-source-${pkgver}.tar.gz)
# source=(http://downloads.sourceforge.net/${pkgname}/${pkgname}-source-${pkgver}.tar.gz)
sha1sums=('52adee7c2bf05834d59231e6a06ff8522203f4de')

build() {
  lupdate ${pkgname}.pro
  lrelease ${pkgname}.pro
  qmake
  make
}

package() {
  install -Dm755 ${pkgname} "${pkgdir}/usr/bin/${pkgname}"
  mkdir -p "${pkgdir}/usr/share/${pkgname}"
  install -m644 ${pkgname}_*.qm "${pkgdir}/usr/share/${pkgname}/"
  install -Dm644 ${pkgname}.desktop "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  for i in 16x16 22x22 24x24 32x32 48x48 256x256; do
      install -D ${pkgname}_${i/x*/}.png "${pkgdir}/usr/share/icons/hicolor/${i}/apps/${pkgname}.png"
  done
}