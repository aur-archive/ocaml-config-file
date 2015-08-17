# Maintainer: charlesthehawk at yahoo dot com
# Contributor: Thomas S Hatch <thatch45 at gmail dot com>
pkgname=ocaml-config-file
pkgver=1.1
pkgrel=3
arch=('i686' 'x86_64')
license=('LGPL')
pkgdesc="OCaml lib to manage application configuration files."
url="http://config-file.forge.ocamlcore.org/"
depends=()
makedepends=('ocaml' 'ocaml-findlib')
source=("https://forge.ocamlcore.org/frs/download.php/845/config-file-$pkgver.tar.gz")
md5sums=('7bc051234ceb29ffd5823ee6bcffe19c')

build() {
  cd "$srcdir/config-file-$pkgver"
  ./configure --prefix=/usr
  make all
  mkdir -p ocamldoc
  make doc
}

package() {
  cd "$srcdir/config-file-$pkgver"
  mkdir -p ${pkgdir}$(ocamlfind printconf destdir)
  mkdir -p $pkgdir/usr/share/doc/ocaml-config-file
  env DESTDIR=${pkgdir} \
      OCAMLFIND_DESTDIR=${pkgdir}$(ocamlfind printconf destdir) \
      OCAMLFIND_LDCONF=ignore \
      ocamlfind install config-file META *.cmi *.cmx *.mli *.cmo *.o
  cp -r ocamldoc/* $pkgdir/usr/share/doc/ocaml-config-file
}
