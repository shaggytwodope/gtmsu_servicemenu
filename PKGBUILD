# Maintainer: pdq <pdq@localhost>
pkgname=gtmsu_servicemenu
pkgver=0.0.1
pkgrel=1
pkgdesc="KDE servicemenu for tmsu. (http://tmsu.org/) - GIT Version"
arch=(any)
url="https://github.com/idk/gtmsu_servicemenu.git"
license=('GPL3')
makedepends=('git')

pkgver_=0.2.2
pkgdesc_="An application that allows you to tag your files to organize them."
url_="http://tmsu.org"
md5sums=('24eb5ed29758a84519c36e322b9c9d3c')
depends=('kdebase-dolphin' 'go-sqlite3' 'go-fuse')
conflicts=('tmsu' 'tmsu-bin')
source=("tmsu-$pkgver_::https://bitbucket.org/oniony/tmsu/downloads/tmsu-i686-${pkgver_}.tgz")
md5sums=('34bb884557bae5f01c4b14ea20c0fe81')

_gitroot="git://github.com/idk/gtmsu_servicemenu.git"
_gitname="gtmsu_servicemenu"

#install=$pkgname.install

build() {
	cd "$srcdir"
	msg "Connecting to GIT server...."

	if [ -d $_gitname ] ; then
		cd $_gitname && git pull origin
		msg "The local files are updated."
	else
		git clone $_gitroot $_gitname
		cd $_gitname
	fi
	msg "GIT checkout done or server timeout"
}

package() {
	cd "$srcdir/$_gitname/"
	install -d "$pkgdir"/usr/share/kde4/services/ServiceMenus
	# Install
	cp -r gtmsu_tag.desktop "$pkgdir"/usr/share/kde4/services/ServiceMenus/gtmsu_tag.desktop

	cd "$srcdir/tmsu-$pkgver_/"
	#mkdir -p $pkgdir/usr/bin
	install -d "$pkgdir"/usr/bin
	cp bin/tmsu "$pkgdir"/usr/bin/
}