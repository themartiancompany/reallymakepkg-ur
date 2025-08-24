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
_pkgver="1.2.3"
_commit="941b9cf0a706597e4dfcdff3f0531350b93ebf01"
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
_archive_sum="639d497492ebe458cf1e005e05439868d28eac20f3227a14a285c8c49cc3e7dc"
_archive_sig_sum="6139fb5213bc6d55f66365b7023641280a29359e69afbb8618e711fe4e5b55bc"
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
  local \
    _TERMUX_PREFIX
  _TERMUX_PREFIX="/data/data/com.termux/files"
  cd \
    "${_tarname}"
  export \
    DESTDIR="${pkgdir}"
  make \
    DESTDIR="${pkgdir}" \
    install
  if [[ "${_os}" == "Android" ]]; then
    _pkgdir="${terdir}"
  elif [[ "${_os}" == "GNU/Linux" ]]; then
    _pkgdir="${pkgdir}"
  fi
  mv \
    "${pkgdir}/etc" \
    "${pkgdir}${_TERMUX_PREFIX}" || \
  true
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${_pkgdir}/usr/share/licenses/${pkgbase}"
}

# vim: ft=sh syn=sh et
