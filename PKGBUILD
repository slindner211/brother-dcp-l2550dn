# Maintainer: Simon D. Lindner <sd[dot][at]pm[dot]me>
# patch idea taken from package brother-hl-l2380dw by apaugh

pkgname=brother-dcp-l2550dn
pkgver=4.0.0_1
pkgrel=1
pkgdesc="LPR and CUPS driver for the Brother DCP-L2550dn"
arch=('x86_64')
url="http://solutions.brother.com/linux"
license=('GPL2' 'custom:Brother EULA')
depends=('cups')
depends_x86_64=('lib32-glibc')
install=${pkgname}.install
source=("http://download.brother.com/welcome/dlf103519/dcpl2550dnpdrv-${pkgver/_/-}.i386.rpm"
	'eula.txt'
	'basedir.patch')
md5sums=('b9cbc4cc2757a382f8c9d93155fc4e3b'
         '8f3fd8004f2345afe1e009bfb9d36f00'
         '153cfd90efef1c38151b22f8259ed261')

prepare() {
	patch -p0 -i basedir.patch
}

package() {
	install -Dm644 eula.txt ${pkgdir}/usr/share/licenses/${pkgname}/eula.txt
	ln -s /usr/share/licenses/GPL2/license.txt ${pkgdir}/usr/share/licenses/${pkgname}/cupswrapper-license.txt
	install -Dm755 ./opt/brother/Printers/DCPL2550DN/cupswrapper/brother-DCPL2550DN-cups-en.ppd ${pkgdir}/usr/share/cups/model/brother-DCPL2550DN-cups-en.ppd
	install -Dm755 ./opt/brother/Printers/DCPL2550DN/cupswrapper/lpdwrapper ${pkgdir}/usr/lib/cups/filter/brother_lpdwrapper_DCPL2550DN
}
