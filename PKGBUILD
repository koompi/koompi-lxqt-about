pkgname=koompi-lxqt-about
pkgver=0.17.0
pkgrel=4
pkgdesc="LXQT about dialog."
arch=("x86_64")
groups=("lxqt")
provides=("lxqt-about")
conflicts=("lxqt-about")
license=("LGPL2.1")
depends=("liblxqt" "libQt5Xdg.so")
makedepends=("lxqt-build-tools" "tar" "gzip")
source=("koompi.svg")
sha256sums=('50e4b89a439466067bb2a5eb3ba010c9cda8c10a64bdd57614556752c946aef8')

prepare(){
	cd "${srdir}"
	git clone --depth 1 https://github.com/koompi/lxqt-about
	mv lxqt-about lxqt-about-${pkgver}-${pkgrel}
}


build() {
	mkdir -p build
	cd build
	cmake "$srcdir/lxqt-about-${pkgver}-${pkgrel}" \
		-DCMAKE_INSTALL_PREFIX=/usr
	make
}

package() {
	cd build
	make DESTDIR="$pkgdir" install

	install -D "${srcdir}/koompi.svg" "${pkgdir}/usr/share/icons/koompi.svg"
}
