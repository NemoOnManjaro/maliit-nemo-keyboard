# $Id$
pkgname=maliit-nemo-keyboard
pkgver=0.104
pkgrel=1
pkgdesc="Contains nemoobile mallit keyboard"
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/maliit-nemo-keyboard"
license=('BSD')
depends=('maliit-framework'
	    'glacier-settings>=0.6.1'
	    'hunspell'
	    'presage')
makedepends=('cmake')
source=("${url}/archive/refs/tags/$pkgver.tar.gz"
        "nemo-keyboard.service")
sha256sums=('822e2e297a1a9a452416180a5aeb1db8b746ec358e8fb7bf6c5a8a0aa5d89eb8'
        '5abe6d0ce4fb22586070fe0700b9c527a1b4ba787d5c32fbeabb95b85ccd8b54')

build() {
    cd $pkgname-$pkgver
    cmake \
        -DCMAKE_INSTALL_PREFIX:PATH='/usr'
    make all
}

package() {
    cd $pkgname-$pkgver
    make DESTDIR="$pkgdir" install
    mkdir -p $pkgdir/usr/lib/systemd/user/graphical-session.target.wants/
    cp ${srcdir}/nemo-keyboard.service $pkgdir/usr/lib/systemd/user/
    ln -s ../nemo-keyboard.service $pkgdir/usr/lib/systemd/user/graphical-session.target.wants/
}
