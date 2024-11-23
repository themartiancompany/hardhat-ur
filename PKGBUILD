# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>
# Contributor: Filipe Bertelli <filipebertelli@tutanota.com>

_node="nodejs"
_pkgbase=hardhat
pkgname="${_pkgbase}"
pkgdesc='Ethereum development environment for professionals'
pkgver=2.22.3
pkgrel=1
arch=(
  'arm'
  'x86_64'
  'mips'
  'i686'
  'pentium4'
  'aarch64'
  'armv7l'
  'armv6l'
)
_ns="NomicFoundation"
url="https://github.com/${_ns}/${_pkgbase}"
license=(
  'custom'
)
depends=(
  "${_node}<23.0"
  'inherits'
)
makedepends=(
  'npm'
)
source=(
  "http://registry.npmjs.org/${_pkgbase}/-/${_pkgbase}-${pkgver}.tgz"
)
noextract=(
  "${_pkgbase}-${pkgver}.tgz"
)
sha512sums=(
  '93c255d8409635c843e9a864836051e70295c58d0e88aa2dedfbb1888a512b47eb46ac8e963711daf2b081648bc3a60878370d340e31c9b8fb3a0ecd4b1af684'
)

package() {
  local \
    _npm_options=()
  _npm_options=(
    -g
    # --user=root
    --prefix="${pkgdir}/usr"
    )
  npm \
    install \
      "${_npm_options[@]}" \
      "${srcdir}/${_pkgbase}-${pkgver}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    -type d \
    -exec \
      chmod \
        755 \
	'{}' \
	+
}

# vim:set sw=2 sts=-1 et:
