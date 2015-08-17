# Contributor: Oliver Kreylos <kreylos@cs.ucdavis.edu>
# Contributor: feilen <feilen1000@gmail.com>

pkgbase=vrui
pkgname=('vrui' 'vrui-demos')
pkgver=3.1
pkgrel=002
arch=('i686' 'x86_64')
url="http://idav.ucdavis.edu/~okreylos/ResDev/Vrui/"
license=('GPL')
depends=( 'zlib' 'libpng' 'libjpeg' 'libtiff' 'alsa-lib' 'speex' 'openal' 'v4l-utils' 'libdc1394' 'bluez' 'libtheora' 'mesa' 'glu'  )
source=( "http://idav.ucdavis.edu/~okreylos/ResDev/Vrui/Vrui-$pkgver-$pkgrel.tar.gz" )
sha1sums=('3c4ded4ed18e4a16394cdc1d625d7d0f4f84b108')

build() {
	#Build main VRUI toolkit
	cd ${srcdir}/Vrui-$pkgver-$pkgrel
	make INSTALLDIR="" SYSTEMINSTALL=1 ${MAKEFLAGS}
	
	#Build Example Programs
	cd ${srcdir}/Vrui-$pkgver-$pkgrel/ExamplePrograms
	make VRUI_MAKEDIR=../BuildRoot INSTALLDIR=/usr RESOURCEINSTALLDIR=/usr/share/VruiExamplePrograms-${pkgver} VRUI_INCLUDEDIR=.. VRUI_LIBDIR=../lib64 ${MAKEFLAGS}
}

package_vrui() {
	cd ${srcdir}/Vrui-$pkgver-$pkgrel

	make SYSTEMINSTALL=1 INSTALLDIR=${pkgdir} install
}

package_vrui-demos() {
	cd ${srcdir}/Vrui-$pkgver-$pkgrel/ExamplePrograms

	make VRUI_MAKEDIR=../BuildRoot INSTALLDIR=${pkgdir}/usr RESOURCEINSTALLDIR=${pkgdir}/usr/share/VruiExamplePrograms-${pkgver} VRUI_INCLUDEDIR=.. VRUI_LIBDIR=../lib64 install
}

#Make the AUR accept split package
pkgname=vrui
pkgdesc="The Vrui VR toolkit aims to support fully scalable and portable applications that run on a range of VR environments."

