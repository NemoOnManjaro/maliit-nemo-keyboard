# $Id$
pkgname=maliit-nemo-keyboard
pkgver=0.108
pkgrel=1
pkgdesc="Contains nemoobile mallit keyboard"
arch=('x86_64' 'aarch64')
url="https://github.com/nemomobile-ux/maliit-nemo-keyboard"
license=('BSD')
depends=(
    'maliit-framework-qt6'
    'glacier-settings'
    'hunspell'
    'hunspell-en_us'
    'presage2>=2.0.1'
    'presage2-lang-en_US'
    'marisa')
makedepends=('cmake' 'qt6-tools')
source=("${url}/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('64e39b2b84b23f4dd813a20ab008c23ebd38a5a73f0fc39377c4bdab1346b8e4')

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
