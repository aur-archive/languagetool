#Maintainer: Andrzej Giniewicz <gginiu@gmail.com>
#Contributor: Julien MISCHKOWITZ <wain@archlinux.fr>
#Contributor: Panagiotis Papadopoulos pano_90 (AT) gmx (DOT) net

pkgname=languagetool
pkgver=1.8
pkgrel=5
pkgdesc="An open source language checker"
arch=('any')
url="http://www.languagetool.org" 
license=("LGPL")
depends=('java-runtime-headless>=6')
makedepends=('unzip')
optdepends=('hunspell: needed for spell checking of some languages'
            'java-runtime: needed for the GUI version'
            'libxtst: needed for the GUI version'
            'gtk2: needed for the GUI version'
            'ttf-dejavu: needed for the GUI version')
install=languagetool.install
source=(http://www.languagetool.org/download/LanguageTool-stable.zip?$pkgver languagetool.sh)
noextract=(LanguageTool-stable.zip?$pkgver)
md5sums=('1982ada9ba7578bce0c377cbe35dd25e'
         '17a63e5abaf8a0ed201137bc9569895e')

package() {
  cd "$srcdir"
  install -d "$pkgdir"/usr/{bin,share/languagetool,share/java/languagetool}
  unzip -q LanguageTool-stable.zip?$pkgver -d "$pkgdir"/usr/share/languagetool
  cd "$pkgdir"/usr/share/languagetool
  rm libhunspell-linux* hunspell-darwin* hunspell-win*
  ln -s /usr/lib/libhunspell-1.3.so libhunspell-linux-x86-32.so
  ln -s /usr/lib/libhunspell-1.3.so libhunspell-linux-x86-64.so
  mv *.jar "$pkgdir"/usr/share/java/languagetool
  install -m755 "$srcdir"/languagetool.sh "$pkgdir"/usr/bin/languagetool
}

