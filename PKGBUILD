# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2023, 2024, 2025  Pellegrino Prevete
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

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (tallero)
#     <pellegrinoprevete@gmail.com>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributor:
#   Marcell Meszaros (MarsSeed)
#     <marcell.meszaros@runbox.eu>

_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_os="$( \
  uname \
    -o)"
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
_py="python"
_py2="${_py}2"
_pkg=reallymakepkg
_pkgname="${_pkg}"
pkgname="${_pkgname}"
_pkgver="1.2.2.1.1"
_commit="37db830aa197b8c4b0396a434d2a50c12de8d502"
pkgver="${_pkgver}"
pkgrel=1
pkgdesc="System-independent makepkg."
arch=(
  'any'
)
_repo="https://github.com"
_ns="themartiancompany"
url="${_repo}/${_ns}/${pkgname}"
license=(
  'AGPL3'
)
depends=(
  'binutils'
  'bash'
  'libcrash-bash'
  'pacman'
)
if [[ "${_os}" == 'Android' ]]; then
  depends+=(
    'libandroid-complex-math'
    'libandroid-glob'
    'libandroid-nl-types'
    'libandroid-posix-semaphore'
    'libandroid-shmem'
    'libandroid-spawn'
    'libandroid-stub'
    'libandroid-support'
    'libandroid-sysv-semaphore'
    'libandroid-utimes'
    'libandroid-wordexp'
  )
fi
makedepends=(
  'make'
)
provides=(
  "recipe-get=${pkgver}"
  "termux-install-shared=${pkgver}"
)
checkdepends=(
  'shellcheck'
)
optdepends=(
  "evmfs: Ethereum Virtual Machine File System resources support"
  "ipfs-dlagent: IPFS resources support"
  "transmission-dlagent: BitTorrent resources support"
  "${_py}-pygments: colorized output and syntax highlighting"
  "${_py2}-pygments: colorized output and syntax highlighting (Python 2)"
)
source=()
sha256sums=()
_url="file://${HOME}/${_pkgname}"
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_archive_sum="6e30cfc5c6868b63501651f4f343e63cfdc2ee48ca2c22985ed7bd43858e586d"
_archive_sig_sum="bd9c8eb52ec12088bc98bc53e68a96bdade6f8d363d07d0b801a9c24836bc763"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.tar.gz::${_evmfs_archive_uri}"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.tar.gz.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="${_archive_sum}"
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)
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
  cd \
    "${_tarname}"
  export \
    DESTDIR="${pkgdir}"
  make \
    DESTDIR="${pkgdir}" \
    install
  if [[ "${_os}" == "Android" ]]; then
    _pkgdir="${terdir}"
  elif [[ "${_os}" == "Android" ]]; then
    _pkgdir="${pkgdir}"
  fi
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${_pkgdir}/usr/share/licenses/${pkgbase}"
}

# vim: ft=sh syn=sh et
