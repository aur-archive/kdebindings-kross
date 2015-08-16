# $Id: PKGBUILD 226490 2014-11-19 17:35:31Z fyan $
# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgbase=kdebindings-kross
pkgname=('kdebindings-kross-python'
#         'kdebindings-kross-ruby'
         'kdebindings-kross-java')
pkgver=4.14.3
pkgrel=1
url="https://projects.kde.org/projects/kde/kdebindings/kross-interpreters"
arch=('i686' 'x86_64')
license=('GPL' 'LGPL' 'FDL')
groups=('kdebindings')
makedepends=('kdelibs' 'cmake' 'automoc4' 'python2' 'java-environment')
source=("http://download.kde.org/stable/${pkgver}/src/kross-interpreters-${pkgver}.tar.xz")
sha1sums=('6be0688d97571422ab4bcac13150d14cfe76c896')

build() {
  cd "${srcdir}"
  mkdir build
  cd build
  cmake ../kross-interpreters-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DKDE4_BUILD_TESTS=OFF \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_ruby=OFF \
    -DPYTHON_EXECUTABLE=/usr/bin/python2
  make
}

package_kdebindings-kross-python() {
  pkgdesc="Python2 language interpreters to enable in-process scripting with Kross"
  depends=('kdelibs' 'python2')

  cd "${srcdir}"/build/python
  make DESTDIR="${pkgdir}" install
}

package_kdebindings-kross-java() {
  pkgdesc="Java language interpreters to enable in-process scripting with Kross"
  depends=('kdelibs' 'java-environment')

  cd "${srcdir}"/build/java
  make DESTDIR="${pkgdir}" install
}

package_kdebindings-kross-ruby() {
  pkgdesc="Ruby language interpreters to enable in-process scripting with Kross"
  depends=('kdelibs' 'ruby')

  cd "${srcdir}"/build/ruby
  make DESTDIR="${pkgdir}" install
}
