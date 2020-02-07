# Maintainer: CapSel <elan1200@capsel.org>
pkgname="elan1200-touchpad-dkms-git"
_pkgbase="hid-elan"
_commit='a54abbfd122032ad33abdd9fffca73115b043e35'
pkgdesc="Kernel module that corrects behaviour of touchpad on ASUS UX310 laptops"

pkgver=2020.02.07
pkgrel=1
makedepends=("git")
arch=("x86_64")
url="https://github.com/CapSel/linux_elan1200_touchpad.git"
source=(
  "git+https://github.com/CapSel/linux_elan1200_touchpad.git#commit=${_commit}"
  "dkms.conf")
sha256sums=(
  "SKIP"
  "1bcc8207a8189920c35d8176fb6c84c707ae6b368645d0c77155b96369392dd6"
)
depends=("lsb-release" "dkms")
provides=("elan1200-touchpad")

package() {
  install -Dm644 dkms.conf "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  cp -r ${srcdir}/linux_elan1200_touchpad/* "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/
}
