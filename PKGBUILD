# Maintainer: Casey Link < unnamedrambler gmail DOT com>
pkgname=qtilities
_realname=JPNaude-Qtilities-44fb841
pkgver=1.0
pkgrel=1
pkgdesc="Building blocks for Qt applications"
arch=('i686' 'x86_64')
url="http://www.qtilities.org"
license=('GPL v3')
depends=('qt')
makedepends=()
source=(JPNaude-Qtilities-44fb841.tar.gz::https://github.com/JPNaude/Qtilities/tarball/v1.0)
md5sums=(4884bb34b0b5e6a6323a0048aeaee093)
provides=('qtilities')


build() {
  cd $srcdir/$_realname/src
  qmake "Qtilities.pro"
  make || return 1
}

package() {
  install -dm755 $pkgdir/usr/lib
  install -dm755 $pkgdir/usr/include
  cd $srcdir/$_realname
  cp -rdp ./bin/* $pkgdir/usr/lib/
  cp -r ./include/* $pkgdir/usr/include/

  # now we overwrite the .h headers 
  MODULES=(Core CoreGui ExtensionSystem Logging ProjectManagement Testing)
  for module in $MODULES; do
    cp -f src/$module/source/*.h $pkgdir/usr/include/Qtilities$module/
  done

}

# vim:set ts=2 sw=2 et:
