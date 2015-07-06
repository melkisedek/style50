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
    mkdir -p ${srcdir}/${pkgname}/opt/style50/bin
	cd "${srcdir}"/${pkgname}
    #create script
    echo "#!/bin/env sh" >> opt/style50/bin/style50 
    echo "env java -jar /opt/style50/style50.jar \$1" >> opt/style50/bin/style50
}

package() {
    mkdir -p "${pkgdir}"/opt/style50/bin
    mkdir -p "${pkgdir}"/usr/bin
	cd "${srcdir}"/${pkgname}

    cp "${srcdir}"/style50.jar "${pkgdir}"/opt/style50/
    cp "${srcdir}"/${pkgname}/opt/style50/bin/style50 "${pkgdir}"/opt/style50/bin/

    install -dm 755 "${pkgdir}/opt/style50/bin"
    ln -s "${srcdir}"/${pkgname}/opt/style50/bin/style50 "${pkgdir}"/usr/bin/style50
    #fix file permissions
    chmod u+x,g+x,o+x "${pkgdir}"/usr/bin/style50