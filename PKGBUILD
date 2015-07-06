# Maintainer: Joschka Thurner <mail@joschkathurner.de>
pkgname=style50
pkgver=1.19
pkgrel=1
pkgdesc="Code style checking tool for CS50 / CS50x (Harvard College's Introduction to Computer Science I)"
arch=('any')
url="https://github.com/melkisedek/style50"
license=('CCPL')
makedepends=('git')
source=(https://github.com/melkisedek/style50/raw/master/style50.jar)
md5sums=('SKIP')
noextract=(style50.jar)

prepare() {
	cd $srcdir 
    mkdir -p "$pkgname/opt/style50/bin" 
    #fix file permissions
    echo "#!/bin/env sh" >> $pkgname/opt/style50/bin/style50 
    echo "env java -jar /opt/style50/style50.jar $1" >> $pkgname/opt/style50/bin/style50 
    find "$pkgname/opt/" -type f -exec chmod 644 {} \;
    chmod 755 "$pkgname/opt/style50"
}

package() {
	mkdir -p "$pkgdir/opt/style50/bin"
	cp "style50.jar" "$pkgdir/opt/style50/"
    install -dm755 "$pkgdir/opt/style50/bin"
    cp -a "$srcdir/$pkgname/opt/" "$pkgdir"
    ln -s "/opt/style50/bin/style50" "$pkgdir/opt/style50/bin/style50"
}
