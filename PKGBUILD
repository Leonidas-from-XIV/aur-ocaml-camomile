# Maintainer: Marek Kubica <marek@xivilization.net>
# Contributor: Serge Zirukin <ftrvxmtrx@gmail.com>
pkgname=ocaml-camomile
pkgver=0.8.5
pkgrel=1
pkgdesc="Comprehensive Unicode library for OCaml"
arch=('i686' 'x86_64')
url="https://github.com/yoriyuki/Camomile"
license=('LGPL')
depends=('ocaml' 'ocaml-findlib>=1.2.3')
source=(https://github.com/yoriyuki/${pkgname/ocaml-}/releases/download/rel-$pkgver/${pkgname/ocaml-/}-$pkgver.tar.bz2)
sha512sums=('ef4da32f955e69e0b2958b4b2bf12ae94e210d8aa7cee5a9030607b79ac43a884758549f3164c223fb07d987a4a50b15f0bc5083ff67120270409f7fb9928014')
options=(!strip !makeflags)

build() {
  cd "$srcdir/${pkgname/ocaml-/}-$pkgver"

  ./configure --prefix=/usr
  mkdir -p $pkgdir$(ocamlfind printconf destdir) || return 1
  mkdir -p $pkgdir/usr/bin
  sed -i -e 's|ocamlfind install|ocamlfind install -destdir '$pkgdir$(ocamlfind printconf destdir)'|' Makefile || return 1
  make || return 1
  make DATADIR="$pkgdir/usr/share" BINDIR="$pkgdir/usr/bin" install
  install -Dm 644 COPYING $pkgdir/usr/share/licenses/$pkgname/LICENSE
}

