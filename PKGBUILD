# Maintainer: Igor Babuschkin <ibabuschkin at gmail dot com>

pkgname=python2-meta-git
pkgver=20121231
pkgrel=1
pkgdesc="Python Meta Programming"
url="https://github.com/numba/Meta"
arch=('i686' 'x86_64')
license=('BSD')
depends=('python2')
makedepends=(git)
provides=('python2-meta')
conflicts=()
replaces=()
backup=()
source=()

_gitroot=https://github.com/numba/Meta.git
_gitname=meta

build() {

  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  python2 setup.py install \
    --prefix=/usr \
    --root=$pkgdir

  mv $pkgdir/usr/bin/depyc{,2}

}
