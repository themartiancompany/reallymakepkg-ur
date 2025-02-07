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

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>
# Contributor: Marcell Meszaros (MarsSeed) <marcell.meszaros@runbox.eu>

_py="python"
_py2="${_py}2"
_git="false"
_offline="false"
_pkg=reallymakepkg
_pkgname="${_pkg}"
pkgname="${_pkgname}"
_pkgver="1.2.1.1.1.1.1.1.1.1.1.1.1.1"
_commit="47fd1a6a30d7be25b9c43f71271eced93786128a"
pkgver="${_pkgver}"
pkgrel=1
pkgdesc="System-independent makepkg"
arch=(
  any
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
makedepends=(
  'make'
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
if [[ "${_git}" == true ]]; then
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
    _sum='a719b5af0cb97df3cc95bf1bd2b5e650852e5a34b4cf71357aead012076aa3df'
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

package() {
  cd \
    "${_tarname}"
  make \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
