# fedoracoin-qt-git Arch PKGBUILD
# Maintainer mxtm <max@mxtm.me>
# Based off of the dogecoin-qt-git PKGBUILD, based off of primecoin-qt's PKGBUILD by Daniel Spies

pkgname=fedoracoin-qt-git
_gitname=fedoracoin
_binname=fedoracoin
pkgver=0.43.da59a37
pkgrel=2
pkgdesc="A QT wallet for the FedoraCoin cryptocurrency, git version."
arch=('x86_64' 'i686')
url="https://bitcointalk.org/index.php?topic=380466.0"
license=('MIT')
provides=('fedoracoin-qt')
conflicts=('fedoracoin-qt')
depends=('qt4' 'miniupnpc' 'boost-libs')
makedepends=('boost' 'gcc' 'make' 'git')
source=('git+https://github.com/fedoracoin/fedoracoin.git'
        'fedoracoin.desktop')
install=fedoracoin-qt-git.install

sha256sums=(SKIP
            'c452d62cfae7c5a5fbb6ce82a50dc844816e9c0517f8216d8ba393cfaf86b88f')

## files & commands for building
_qmake=qmake-qt4

pkgver() {
	cd ${_gitname}
	echo $(git describe --always | sed 's/-/./g')
}
    

build() {
	cd ${_gitname}

	${_qmake} ${_binname}-qt.pro
		
	make ${MAKEFLAGS} || make ${MAKEFLAGS}
}

package() {
	install -Dm644 ${_binname}.desktop ${pkgdir}/usr/share/applications/${_binname}.desktop

	cd ${_gitname}
	install -Dm755 ${_binname}-qt "$pkgdir"/usr/bin/${_binname}-qt
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
	install -Dm644 src/qt/res/icons/bitcoin.png "$pkgdir"/usr/share/pixmaps/${_binname}.png
}
