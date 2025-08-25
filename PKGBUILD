pkgname=attr
pkgver=2.5.2
pkgrel=1
pkgdesc="Extended attribute support library for ACL support"
arch=('x86_64')
url="https://savannah.nongnu.org/projects/attr"
license=(
    'GPL-2.0-or-later'
    'LGPL-2.1-or-later'
)
depends=('glibc')
backup=(etc/xattr.conf)
options=('!lto')
source=(https://download.savannah.gnu.org/releases/${pkgname}/${pkgname}-${pkgver}.tar.gz)
sha256sums=(39bf67452fa41d0948c2197601053f48b3d78a029389734332a6309a680c6c87)

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        --disable-static
        --sysconfdir=/etc
        --docdir=/usr/share/doc/${pkgname}-${pkgver}
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install
}
