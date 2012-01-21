# $Id: PKGBUILD 51492 2011-07-10 19:48:13Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>
# Packager: Ian D Brunton <iandbrunton@gmail.com>

pkgname=dwm
pkgver=5.9
pkgrel=2
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
groups=(customised)
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama')
install=dwm.install
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
	http://hg.punctweb.ro/dwm/raw/bf9d3fe96f23/01-dwm-5.9-pertag2.diff
	http://hg.punctweb.ro/dwm/raw/bf9d3fe96f23/05-dwm-5.9-gaps.diff
	http://hg.punctweb.ro/dwm/raw/bf9d3fe96f23/09-dwm-5.9-focusonclick.diff
	http://dwm.suckless.org/patches/dwm-5.7.2-attachaside.diff
	http://hg.punctweb.ro/dwm/raw/bf9d3fe96f23/02-dwm-5.9-push.diff
	statuscolors.diff
	centredfloating.diff
	config.h
	dwm.desktop)

build() {
  cd $srcdir/$pkgname-$pkgver
  cp $srcdir/config.h config.h
  patch -Np1 -i $srcdir/dwm-5.7.2-attachaside.diff
  patch -Np1 -i $srcdir/01-dwm-5.9-pertag2.diff
  patch -Np1 -i $srcdir/02-dwm-5.9-push.diff
  patch -Np1 -i $srcdir/05-dwm-5.9-gaps.diff
  patch -Np1 -i $srcdir/09-dwm-5.9-focusonclick.diff
  patch -Np1 -i $srcdir/centredfloating.diff
  sed -i 's/CPPFLAGS =/CPPFLAGS +=/g' config.mk
  sed -i 's/^CFLAGS = -g/#CFLAGS += -g/g' config.mk
  sed -i 's/^#CFLAGS = -std/CFLAGS += -std/g' config.mk
  sed -i 's/^LDFLAGS = -g/#LDFLAGS += -g/g' config.mk
  sed -i 's/^#LDFLAGS = -s/LDFLAGS += -s/g' config.mk
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR=$pkgdir install
  install -m644 -D LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -m644 -D README $pkgdir/usr/share/doc/$pkgname/README
  install -m644 -D $srcdir/dwm.desktop $pkgdir//etc/X11/sessions/dwm.desktop
}

md5sums=('2799f885c05817ca112d521bb247f797'
         '7739f58d54c4c4f8a59bc98e19d39baa'
         '996ae82928a94055e7031a53b7106063'
         'b795be2544469a196663fa48f2168b55'
         'a92ee04c33b1082da61b55d3617249eb'
         '43851630c3b35ceb5c4f0a24f5305da1'
         'ffc4f7ac30402277451044a52c79d174'
         '0065c66daa107b282efd8144de5b393a'
         'c69d2fc30884c7d440b2a22e746ac09f'
         '939f403a71b6e85261d09fc3412269ee')
