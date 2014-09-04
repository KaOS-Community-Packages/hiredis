pkgname=hiredis
pkgver=0.11.0
pkgrel=1
pkgdesc='Minimalistic C client library for Redis'
arch=('x86_64')
url="https://github.com/redis/hiredis/"
license=('BSD')
depends=('glibc')
checkdepends=('redis')
source=(hiredis-$pkgver.tar.gz::https://github.com/redis/$pkgname/archive/v$pkgver.tar.gz)
sha256sums=('ff7b2849e55bf3589eecced7125934feb9645c36a4d490d001dc08c93553eafd')

build() {
  cd "$srcdir"/$pkgname-$pkgver
  make
}

check() {
  cd "$srcdir"/$pkgname-$pkgver
  sed -r 's|echo \\|echo -e \\|' -i Makefile
  make check
}

package() {
  cd "$srcdir"/$pkgname-$pkgver
  make PREFIX="$pkgdir"/usr install

  install -Dm 644 COPYING "$pkgdir"/usr/share/licenses/$pkgname/COPYING
}
