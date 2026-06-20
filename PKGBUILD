_release_url=$(curl -Ls -o /dev/null -w "%{url_effective}" https://github.com/CachyOS/proton-cachyos/releases/latest)
_tag=${_release_url##*/}
_base=${_tag#cachyos-}
_base=${_base%-slr}

pkgname=proton-cachyos-v3-bin
_pkgname=proton-cachyos
pkgver=${_base//-/.}
pkgrel=1
pkgdesc="A compatibility tool for Steam Play (Pre-compiled x86_64_v3 SLR release)"
url="https://github.com/CachyOS/proton-cachyos"
arch=('x86_64_v3' 'x86_64')
license=('custom')
options=('!strip' '!buildflags' '!debug' 'staticlibs')

depends=('python')
makedepends=('curl')
provides=(
	'proton'
	'proton-cachyos'
	'proton-cachyos-slr'
)
conflicts=(
	'proton-cachyos'
	'proton-cachyos-bin'
	'proton-cachyos-native'
	'proton-cachyos-slr'
)

source=(
	"https://github.com/CachyOS/proton-cachyos/releases/download/${_tag}/proton-cachyos-${_base}-slr-x86_64_v3.tar.xz"
)
sha256sums=('SKIP')

package() {
	local _compatdir="${pkgdir}/usr/share/steam/compatibilitytools.d/${_pkgname}"
	install -d "${_compatdir}"

	local _extracted_dir
	_extracted_dir=$(find "${srcdir}" -mindepth 1 -maxdepth 1 -type d -name "proton-cachyos-*" | head -n 1)
	cp -a "${_extracted_dir}/"* "${_compatdir}/"
}
