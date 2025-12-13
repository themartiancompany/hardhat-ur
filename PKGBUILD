# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Filipe Bertelli
#     <filipebertelli@tutanota.com>

_node="nodejs"
_pkg=hardhat
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
_pkgdesc=(
  "Ethereum development"
  "environment."
)
pkgdesc="${_pkgdesc[*]}"
pkgver=2.22.3
_commit="1bb6f45662c9688a552cece2cc2e95a3929b543d"
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
url="https://github.com/${_ns}/${_pkg}"
license=(
  'custom'
)
depends=(
  "${_node}<23.0"
  # "inherits"
)
makedepends=(
  'npm'
)
_tarname="${_pkg}-${pkgver}"
_npm_sum="9e17a5fced5da0b72db8d91d986dfa815c6f1d04542edc34c6008e63ae783fbb"
_npm_sig_sum="46f0e9454e4789efbda023956716a22f5259afa526ab7b0d765d157a1898f0d9"
if [[ "${_npm}" == "true" ]]; then
  _sum="${_npm_sum}"
  _sig_sum="${_npm_sig_sum}"
fi
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_npm_uri}"
    _sum="${_npm_sum}"
    _sig_src="${_npm_sig_src}"
    _sig_sum="${_npm_sig_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="${_bundle_uri}"
      _sum="${_bundle_sum}"
      _sig_src="${_bundle_sig_src}"
      _sig_sum="${_bundle_sig_sum}"
    elif [[ "${_git}" == "false" ]]; then
      _uri="${_evmfs_uri}"
      _sig_src="${_evmfs_sig_src}"
    fi
  fi
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/@${_ns}/${_pkg}/-/${_tarfile}"
  elif [[ "${_npm}" == "false" ]]; then
    _uri="${url}"
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_npm}" == "true" ]]; then
  noextract=(
    "${_tarfile}"
  )
fi
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
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
