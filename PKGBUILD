# $Id$
pkgname=maliit-nemo-keyboard
pkgver=0.102.1
pkgrel=1
pkgdesc="Contains the reference input method plugins, such as the Maliit Keyboard. "
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/maliit-nemo-keyboard"
license=('BSD')
depends=('maliit-framework'
	    'glacier-settings>=0.6.1')
makedepends=('cmake')
source=("${url}/archive/refs/tags/$pkgver.tar.gz"
        "nemo-keyboard.service")
sha256sums=('8d06adb5826a0fec231f5ee517320a8d984cf71fb3ba93aaa19f489081863d0c'
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
