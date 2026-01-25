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

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (tallero)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributor:
#   Marcell Meszaros (MarsSeed)
#     <marcell.meszaros@runbox.eu>

_evmfs_available="$(
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
_os="$(
  uname \
    -o)"
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="gitlab"
fi
if [[ ! -v "_doc" ]]; then
  _doc="true"
fi
if [[ "${_evmfs}" == "true" ]] || \
   [[ "${_git_http}" == "gitlab" ]]; then
  _archive_format="tar.gz"
elif [[ "${_git_http}" == "github" ]]; then
  _archive_format="zip"
fi
_py="python"
_py2="${_py}2"
_pkg=reallymakepkg
_pkgname="${_pkg}"
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_doc}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
_pkgver="1.2.5"
_commit="526b0f423cd3c826db44f357ac3c819e4987e8ff"
pkgver="${_pkgver}"
pkgrel=6
_pkgdesc=(
  "System-independent makepkg."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_repo="https://${_git_http}.com"
_ns="themartiancompany"
url="${_repo}/${_ns}/${_pkg}"
license=(
  'AGPL3'
)
depends=(
  'binutils'
  'bash'
  'gawk'
  'libcrash-bash'
  'pacman'
  'sed'
  'tar'
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
if [[ "${_doc}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
provides=(
  "package-info-get=${pkgver}"
  "recipe-get=${pkgver}"
  "termux-install-shared=${pkgver}"
)
checkdepends=(
  'shellcheck'
)
_evmfs_optdepends=(
  "evmfs:"
    "Ethereum Virtual Machine"
    "File System resources support."
)
_ipfs_dlagent_optdepends=(
  "ipfs-dlagent:"
    "IPFS resources support."
)
_py2_pygments_optdepends=(
  "${_py2}-pygments:"
    "colorized output and"
    "syntax highlighting"
)
_py_pygments_optdepends=(
  "${_py}-pygments:"
    "colorized output and syntax"
    "highlighting."
)
_transmission_dlagent_optdepends=(
  "transmission-dlagent:"
    "BitTorrent resources support."
)
optdepends=(
  "${_evmfs_optdepends[*]}"
  "${_ipfs_dlagent_optdepends[*]}"
  "${_transmission_dlagent_optdepends[*]}"
  "${_py2_pygments_optdepends[*]}"
  "${_py_pygments_optdepends[*]}"
)
provides=(
  "recipe-get=${pkgver}"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${_pkg}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${_pkg}"
fi
_sum="6b70dd2f6c347d448c2d6140fdb70429d17135e6713ea6c095df1b34e4010e6a"
_sig_sum="75e32fa522ae3e2a82993ef9bdf5a9c312860078264fba06cebf920349a914ec"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarname}.${_archive_format}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarname}.${_archive_format}.sig::${_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_git}" == "false" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
  fi
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == "true" ]]; then
    makedepends+=(
      "git"
    )
    _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
    _sum="SKIP"
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_http}" == "gitlab" ]]; then
      if [[ "${_tag_name}" == 'pkgver' ]]; then
        _uri="${_url}/archive/refs/tags/${_tag}.${_archive_format}"
      else
        _uri=""
      fi
      _src="${_tarname}.${_archive_format}::${_uri}"
    elif [[ "${_git_http}" == "github" ]]; then
      if [[ "${_tag_name}" == "commit" ]]; then
        _src="${_tarname}.${_archive_format}::${_url}/archive/${_commit}.${_archive_format}"
      fi
    fi
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

package_reallymakepkg() {
  local \
    _TERMUX_PREFIX \
    _make_opts=()
  _make_opts+=(
    DESTDIR="${pkgdir}"
  )
  _TERMUX_PREFIX="/data/data/com.termux/files"
  conflicts=(
    "package-info-get"
    "recipe-get"
  )
  cd \
    "${_tarname}"
  export \
    DESTDIR="${pkgdir}"
  make \
    "${_make_opts[@]}" \
    install-configs
  make \
    "${_make_opts[@]}" \
    install-scripts
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
    "${_pkgdir}/usr/share/licenses/${pkgname}"
}

package_reallymakepkg-docs() {
  local \
    _TERMUX_PREFIX \
    _make_opts=()
  provides=()
  _make_opts+=(
    DESTDIR="${pkgdir}"
  )
  _TERMUX_PREFIX="/data/data/com.termux/files"
  pkgdesc="${_pkgdesc[*]} (documentation)."
  cd \
    "${_tarname}"
  export \
    DESTDIR="${pkgdir}"
  make \
    "${_make_opts[@]}" \
    install-doc
  make \
    "${_make_opts[@]}" \
    install-man
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${_pkgdir}/usr/share/licenses/${pkgname}"
}

# vim: ft=2 syn=sh et
