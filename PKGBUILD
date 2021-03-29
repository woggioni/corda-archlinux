# Contributor: Walter Oggioni <walter.oggioni@r3.com>                
# Maintainer: Walter Oggioni <walter.oggioni@r3.com>
pkgname=corda-cli-git
_basename="${pkgname%-git}"
pkgver=67.0791d7a
pkgrel=1
pkgdesc="Command Line Interface Utility to deploy a Corda Network"
arch=('i686' 'x86_64' 'armv7h' 'aarch64')
url="https://github.com/corda/corda-cli"
license=('GPL')
makedepends=('unzip')
depends=('java-runtime')
source=(git+ssh://git@github.com/corda/corda-cli.git)
md5sums=('SKIP')

pkgver() {
  cd $srcdir/$_basename
  echo $(git rev-list --count main).$(git rev-parse --short main)
}

build() {
    cd $srcdir/$_basename
    ./gradlew installDist
}

package() {
  _build="$srcdir/$_basename/build/install/$_basename"
  install -d "$pkgdir/usr/share/java/$_basename/"{bin,lib}
  install -m644 "$_build/lib/"*.jar "$pkgdir/usr/share/java/$_basename/lib"
  install -m755 "$_build/bin/$_basename" "$pkgdir/usr/share/java/$_basename/bin"
  install -d "$pkgdir/usr/bin"
  ln -s "/usr/share/java/$_basename/bin/$_basename" "$pkgdir/usr/bin/$_basename" 
}

