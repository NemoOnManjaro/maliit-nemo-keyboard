# $Id$
pkgname=maliit-nemo-keyboard
pkgver=0.105
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
source=("${url}/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('67fe3fd0ea4c8bc8106e105fe68f2f861ef89caeba76c58ff1946241bb14f71b')

build() {
    cd $pkgname-$pkgver
    cmake \
        -DCMAKE_INSTALL_PREFIX:PATH='/usr'
    make all
}

package() {
    cd $pkgname-$pkgver
    make DESTDIR="$pkgdir" install
    mkdir -p $pkgdir/usr/lib/systemd/user/user-session.target.wants/
    ln -s ../maliit-server.service $pkgdir/usr/lib/systemd/user/user-session.target.wants/
}
