# Maintainer: Sung Pae <self@sungpae.com>
pkgname=openj
pkgver=7.01.045
pkgrel=2
pkgdesc="The J programming language"
arch=('x86_64')
url="http://www.jsoftware.com/"
license=('GPL3')
groups=('guns')

pkgver() {
    cd "$startdir"
    cat j/system/config/version.txt
}

prepare() {
    cd "$startdir"
    mkdir -p 'build'
    cd 'build'
    cmake -DCMAKE_INSTALL_PREFIX=/usr ..
}

build() {
    cd "$startdir/build"
    make -j $(grep -c ^processor /proc/cpuinfo)
}

package() {
    cd "$startdir/build"
    make DESTDIR="$pkgdir/" install
    mv "$pkgdir"/usr/bin/{jconsole,J}
}
