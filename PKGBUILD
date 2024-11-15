# Maintainer: Patrick Northon <northon_patrick3@yahoo.ca>
# Contributor: René Wagner <rwa at clttr dot info>
# Contributor: Juan Simón <play4pro at protonmail dot com>
# Contributor: alium
# Contributor: angelsl
# Contributor: hayao <hayao@fascode.net>

_pkgbase=r8168
pkgname=${_pkgbase}-dkms
pkgver=8.054.00
pkgrel=1
pkgdesc="A kernel module for Realtek 8168 network cards (DKMS version) (betel)"
url="https://github.com/lustryrose882/$_pkgbase"
license=("GPL")
arch=('i686' 'x86_64')
depends=('glibc' 'dkms')
makedepends=()
conflicts=("${_pkgbase}" "r8169-dkms")
provides=("${_pkgbase}")
source=('dkms.conf')
sha256sums=('SKIP')

package() {
	install -Dm644 'dkms.conf' "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/dkms.conf"

	sed -e "s/@PKGNAME@/${_pkgbase}/g" \
	    -e "s/@PKGVER@/${pkgver}/g" \
	    -i "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/dkms.conf"

	ls -l
	cp -dr --no-preserve='ownership' "./${_pkgbase}" "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/src"

	echo "blacklist r8169" | \
		install -Dm644 '/dev/stdin' "$pkgdir/usr/lib/modprobe.d/$pkgname.conf"
}
