# $Id$
pkgname=maliit-nemo-keyboard
pkgver=1.0
pkgrel=1
pkgdesc="Nemomobile keyboard"
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
sha256sums=('e4ee02f3d165b57bfb2f42408e4db783191fcea5e03f27f36c93b53f6cd2f857')

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
