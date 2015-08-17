# Maintainer: Alexander Monakov <amonakov@gmail.com>

pkgname=primus-git
pkgver=20130420
pkgrel=1
pkgdesc="Faster OpenGL offloading for Bumblebee (git sources)"
arch=('i686' 'x86_64')
url="https://github.com/amonakov/primus"
license=('custom:ISC')
depends=('bumblebee' 'mesa-libgl' 'nvidia-utils')
makedepends=('git')
provides=('primus')
conflicts=('primus')
source=(git://github.com/amonakov/primus.git)
sha1sums=('SKIP')

pkgver() {
  date +%Y%m%d
}

build() {
  cd primus

  make
}

package() {
  cd primus

  install -D "lib/libGL.so.1" "$pkgdir/usr/lib/primus/libGL.so.1"
  sed -e "s#^PRIMUS_libGL=.*#PRIMUS_libGL='/usr/\$LIB/primus'#" primusrun > primusrun.dist
  install -D "primusrun.dist" "$pkgdir/usr/bin/primusrun"

  install -D "primus.bash-completion" "$pkgdir/etc/bash_completion.d/primusrun"

  gzip -9 "primusrun.1"
  install -D "primusrun.1.gz" "$pkgdir/usr/share/man/man1/primusrun.1.gz"

  install -D -m644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
