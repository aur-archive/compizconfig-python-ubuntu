# Maintainer: Xiao-Long Chen <chenxiaolong@cxl.epac.to>

pkgname=compizconfig-python-ubuntu
_ubuntu_rel=0ubuntu4
pkgver=0.9.5.94.${_ubuntu_rel}
pkgrel=102
pkgdesc="Compizconfig bindings for python - Ubuntu version"
arch=('i686' 'x86_64')
url="http://compiz.org"
license=('GPL')
depends=('compiz-core-ubuntu' 'libcompizconfig-ubuntu' 'glib2' 'python2' 'pyrex')
makedepends=('intltool' 'pkgconfig' 'cython2')
provides=('compizconfig-python')
conflicts=('compizconfig-python')
groups=('unity')
source=("https://launchpad.net/ubuntu/+archive/primary/+files/${pkgname%-*}_${pkgver%.*}.orig.tar.gz"
        "https://launchpad.net/ubuntu/+archive/primary/+files/${pkgname%-*}_${pkgver%.*}-${_ubuntu_rel}.diff.gz")
sha512sums=('88bb4e9f481351209c2b05d0f921f86ab4c73ed1dc3db47f9f341b408d6327fbc80adc3901c3e8dc0e5272c0b45cead09c50986b264c01eac94067da2ee6b536'
            '38397cf2d82387101bdf0eda1d2a721166111e8fbbcab87602ecbd577413f9e876fe91a677990ae4b24551be710c2cee37389a205aa0aede9775c6beebc489e7')

build() {
  cd "${srcdir}/${pkgname%-*}-${pkgver%.*}"

  # Apply Ubuntu patches
  patch -Np1 -i "${srcdir}/compizconfig-python_${pkgver%.*}-${_ubuntu_rel}.diff"
  for i in $(cat debian/patches/series | grep -v '#'); do
    patch -Np1 -i "debian/patches/${i}"
  done

  python2 setup.py build
}

package() {
  cd "${srcdir}/${pkgname%-*}-${pkgver%.*}"

  python2 setup.py install --prefix="/usr" --root="${pkgdir}"
}
