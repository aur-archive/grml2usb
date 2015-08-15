# Contributor: Florian Ziegler <zieglerflorian fastmail fm>
pkgname=grml2usb
pkgver=0.14.0
pkgrel=1
pkgdesc="Installs one or multiple grml ISOs on an USB device - contains grml2iso"
arch=(i686 x86_64)
options=(!strip)
url="http://grml.org/grml2usb/"
license=('GPL2')
depends=('python2' 'bash')
optdepends=('cdrkit: creating multiboot ISOs with grml2iso')
source=(deb_package_${pkgver}_${pkgrel}_i386.deb::http://deb.grml.org/pool/main/g/grml2usb/${pkgname}_${pkgver}_i386.deb)
noextract=(deb_package_${pkgver}_${pkgrel}_i386.deb deb_package_${pkgver}_${pkgrel}_i386.deb)
md5sums=('bb95f4f6a5a4d5540e18d58657eca942')

build() {
  cd "$srcdir"

  bsdtar -xf deb_package_${pkgver}_${pkgrel}_i386.deb
  bsdtar -xf data.tar.gz

  mkdir -p ${pkgdir}/usr/sbin/
  mkdir -p ${pkgdir}/usr/share/man/man8
  mkdir -p ${pkgdir}/usr/share/grml2usb
  mkdir -p ${pkgdir}/usr/share/grml2usb/grub
  mkdir -p ${pkgdir}/usr/share/doc
  mkdir -p ${pkgdir}/usr/share/doc/grml2usb
  mkdir -p ${pkgdir}/usr/share/grml2usb/mbr

  install -m 755 usr/sbin/grml2usb ${pkgdir}/usr/sbin/grml2usb
  #nstall -m 755 usr/sbin/grml2usb-compat ${pkgdir}/usr/sbin/grml2usb-compat
  install -m 755 usr/sbin/grml2iso ${pkgdir}/usr/sbin/grml2iso

  sed -i'' -e '1s/python/python2/' ${pkgdir}/usr/sbin/grml2usb
  sed -i'' -e '1s/python/python2/' ${pkgdir}/usr/sbin/grml2iso
  #sed -i'' -e '1s/python/python2/' ${pkgdir}/usr/sbin/grml2usb-compat

  install -m 644 usr/share/man/man8/grml2usb.8.gz ${pkgdir}/usr/share/man/man8/grml2usb.8.gz
  install -m 644 usr/share/man/man8/grml2iso.8.gz ${pkgdir}/usr/share/man/man8/grml2iso.8.gz
  #nstall -m 644 usr/share/man/man8/grml2usb-compat.8.gz ${pkgdir}/usr/share/man/man8/grml2usb-compat.8.gz

  install -m 644 usr/share/grml2usb/grub/splash.xpm.gz ${pkgdir}/usr/share/grml2usb/grub/splash.xpm.gz
  install -m 644 usr/share/grml2usb/grub/grml.png ${pkgdir}/usr/share/grml2usb/grub/grml.png

  #nstall -m 755 usr/share/grml2usb/lilo/lilo.static.amd64 ${pkgdir}/usr/share/grml2usb/lilo/lilo.static.amd64
  #nstall -m 755 usr/share/grml2usb/lilo/lilo.static.i386 ${pkgdir}/usr/share/grml2usb/lilo/lilo.static.i386

  install -m 644 usr/share/grml2usb/mbr/mbrmgr ${pkgdir}/usr/share/grml2usb/mbr/mbrmgr
  install -m 644 usr/share/grml2usb/mbr/mbrldr ${pkgdir}/usr/share/grml2usb/mbr/mbrldr

  install -m 644 usr/share/doc/grml2usb/changelog.gz ${pkgdir}/usr/share/doc/grml2usb/changelog.gz
  install -m 644 usr/share/doc/grml2usb/copyright ${pkgdir}/usr/share/doc/grml2usb/copyright
  install -m 644 usr/share/doc/grml2usb/NEWS.Debian.gz ${pkgdir}/usr/share/doc/grml2usb/NEWS.Debian.gz
  install -m 644 usr/share/doc/grml2usb/TODO ${pkgdir}/usr/share/doc/grml2usb/TODO
}
