# $Id$

pkgname=maliit-nemo-keyboard

pkgver=0.100

pkgrel=1
pkgdesc="Contains the reference input method plugins, such as the Maliit Keyboard. "
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/maliit-nemo-keyboard"
license=('BSD')
depends=('maliit-framework')
makedepends=('cmake')
source=("${url}/archive/refs/tags/$pkgver.tar.gz"
        "nemo-keyboard.service")
sha256sums=('042f98ef2bbf48b3a06b6c67591b8f00c502bf9c9c108f57e472c5716e3731a5' 
        'ff03fb71dd600b0da1c28429fd9623ba744467715930dab02758cb0205979cbe')

build() {
    cmake \
        -B "${pkgname}/build" \
        -S "${pkgname}" \
        -DCMAKE_INSTALL_PREFIX:PATH='/usr'
    make -C "${pkgname}/build" all
}

package() {
    make -C "${srcdir}/${pkgname}/build" DESTDIR="$pkgdir" install
    mkdir -p $pkgdir/usr/lib/systemd/user/graphical-session.target.wants/
    cp ${srcdir}/nemo-keyboard.service $pkgdir/usr/lib/systemd/user/
    ln -s ../nemo-keyboard.service $pkgdir/usr/lib/systemd/user/graphical-session.target.wants/
}
