# Maintainer: Tomás Pinho <me(at)tomaspinho(dot)com>

pkgname=rtl8821ce-dkms-git
_pkgbase=rtl8821ce
pkgver=1.0.5.r140.gbe733dc
pkgrel=1
pkgdesc="rtl8821CE driver with firmware"
arch=('i686' 'x86_64')
url="https://github.com/tomaspinho/rtl8821ce"
license=('GPL2')
depends=('dkms')
makedepends=('git')
conflicts=("${_pkgbase}")
source=("git+https://github.com/tomaspinho/rtl8821ce.git"
         rtl8821ce-5.19.2.patch)
#        'dkms.conf')
sha256sums=('SKIP'
            '06f9cb136782ac075eaa513cebe25e8b789abe2bfd3e04394271020aa111b228')
#            '3f401c2a8c862af919b1fdaaa4270ef18f674725035c9769590d529b9aa5c078')

prepare() {
    cd rtl8821ce
    patch -Np1 -i ../rtl8821ce-5.19.2.patch
}

pkgver() {
    cd rtl8821ce
    printf '%s.r%s.g%s' '1.0.5' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
        cd rtl8821ce
        mkdir -p "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}
        cp -pr * "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}
        #cp ${srcdir}/dkms.conf ${pkgdir}/usr/src/${_pkgbase}-${pkgver}
        # Set name and version
        sed -e "s/@_PKGBASE@/${_pkgbase}-dkms/" \
                        -e "s/@PKGVER@/${pkgver}/" \
                        -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf
}
