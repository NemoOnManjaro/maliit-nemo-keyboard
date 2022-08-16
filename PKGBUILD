# $Id$

pkgname=maliit-nemo-keyboard

pkgver=0.101

pkgrel=1
pkgdesc="Contains the reference input method plugins, such as the Maliit Keyboard. "
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/maliit-nemo-keyboard"
license=('BSD')
depends=('maliit-framework')
makedepends=('cmake')
source=("${url}/archive/refs/tags/$pkgver.tar.gz"
        "nemo-keyboard.service")
sha256sums=('a0a9d3c633a4f8b47d7db7263932dea5616773e8b618f7eb350f45f8cf1cf1cb' 
        'ff03fb71dd600b0da1c28429fd9623ba744467715930dab02758cb0205979cbe')

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
