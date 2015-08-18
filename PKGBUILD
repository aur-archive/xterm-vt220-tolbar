#
# Maintainer: Alexej Magura <agm2819*gmail*>
#
# Contributor: Jan de Groot <jgc@archlinux.org>
# Contributor: Alexander Baldeck <alexander@archlinux.org>

pkgname=xterm-vt220-tolbar
_pkgname=xterm
pkgver=300
pkgrel=1
pkgdesc="X Terminal Emulator, use VT220 for terminal w/ enabled tolbar"
arch=('i686' 'x86_64')
#url="http://invisible-island.net/xterm/"
url="ftp://invisible-island.net/xterm/"
license=('custom')
depends=('libxft' 'libxaw')
conflicts=('xterm')
provides=('xterm')
options=('ccache')
source=("ftp://invisible-island.net/$_pkgname/$_pkgname-$pkgver.tgz"
        "LICENSE"
	"Makefile")
md5sums=('6adc7c7f39ab2a71fd83747049d60358'
         '10ecc3f8ee91e3189863a172f68282d2'
         '96c86ee493b1cd69b5962f3e062cfd56')

prepare() {
    cd $srcdir/$_pkgname-$pkgver

    ./configure \
	--prefix=/usr \
	--libdir=/etc \
	--mandir=/usr/share/man \
	--with-app-defaults=/usr/share/X11/app-defaults/ \
	--with-x \
	--disable-full-tgetent \
	--disable-imake \
	--with-terminal-is=vt220 \
	--enable-ansi-color \
	--enable-88-color \
	--enable-256-color \
	--enable-broken-osc \
	--enable-broken-st \
	--enable-load-vt-fonts \
	--enable-i18n \
	--enable-toolbar \
	--enable-wide-chars \
	--enable-doublechars \
	--enable-warnings \
	--enable-tcap-query \
	--enable-logging \
	--enable-dabbrev \
	--enable-freetype \
	--enable-luit \
	--enable-mini-luit \
	--enable-16bit-chars \
	--enable-narrowproto \
	--enable-exec-xterm \
	--with-tty-group=tty \
	--with-utmp-setgid=utmp
}
		 

build() {
    cd $srcdir/$_pkgname-$pkgver
    make

}

package() {
    cd $srcdir/$_pkgname-$pkgver
    
    make DESTDIR=$pkgdir install

    cd "$srcdir" 

    make PKGNAME=$_pkgname PREFIX=$pkgdir DESTDIR=\$\(PREFIX\)/usr/share/licenses/$pkgname SRCIX=$srcdir fix-all 
    
    #make clean
}
