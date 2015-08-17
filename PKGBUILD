# $Id: PKGBUILD 82 2009-07-17 19:56:55Z aaron $
# Maintainer: Roman Kyrylych <roman@archlinux.org>
# Contributor: William Rea <sillywilly@gmail.com>

pkgname=serpentine
pkgver=0.9
pkgrel=3
pkgdesc="An application for writing CD-Audio discs"
arch=('i686' 'x86_64')
url="https://launchpad.net/serpentine"
license=('GPL')
depends=('gnome-python-desktop' 'gstreamer0.10-python' 'nautilus-cd-burner' \
         'pyxml' 'gconf>=2.18.0.1-4' 'desktop-file-utils' 'totem-plparser')
makedepends=('intltool')
install=serpentine.install
source=(https://launchpad.net/debian/lenny/+source/${pkgname}/${pkgver}-6/+files/${pkgname}_${pkgver}.orig.tar.gz)
md5sums=('d7b07fdcf1533cd75f051a910e57b909')

build() {
    cd "${pkgname}-$pkgver"
    ./configure --prefix=/usr
    make
}

package() {
    make GCONF_DISABLE_MAKEFILE_SCHEMA_INSTALL=1 DESTDIR=$pkgdir install

    mkdir -p "$pkgdir/usr/share/gconf/schemas"
    gconf-merge-schema "$pkgdir/usr/share/gconf/schemas/${pkgname}.schemas" \
                       "$pkgdir/etc/gconf/schemas/*.schemas"
    rm -f "$pkgdir/etc/gconf/schemas/"*.schemas
}
