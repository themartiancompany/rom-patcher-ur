# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$(
  uname \
    -o)"
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
_node="nodejs"
if [[ "${_os}" == "Android" ]]; then
  _node="nodejs-lts"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_tag_name" ]]; then
  _tag_name="commit"
fi
_Pkg=RomPatcher.js
_pkg=rom-patcher
_commit="6e7ce4539eb3ff3f9aebd2c9f1493c19f576eee0"
_pkgver=3.2.1
_pkgver_module="3.0.0"
if [[ ! -v "_tag" ]]; then
  if [[ "${_tag_name}" == "commit" ]]; then
    _tag="${_commit}"
  fi
fi
if [[ ! -v "_npm" ]]; then
  _npm="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
_archive_format="tgz"
if [[ ! -v "${_archive_format}" ]]; then
  if [[ "${_npm}" == "false" ]]; then
    if [[ "${_git_http}" == "github" ]]; then
      _archive_format="zip"
    fi
  fi
fi
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgdesc=(
  "A ROM patcher made in Javascript."
)
pkgdesc="${_pkgdesc[*]}"
pkgver="${_pkgver}.1"
if [[ "${_npm}" == "true" ]]; then
  pkgver="${_pkgver}"
fi
pkgrel=1
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="marcrobledo"
_ns="themartiancompany"
url="${_http}/${_ns}/${_Pkg}"
license=(
  'MIT'
)
depends=(
  "${_node}"
)
provides=(
  "${_node}-${_pkg}=${pkgver}"
)
makedepends=(
  "npm"
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
fi
_url="${url}"
_tarname="${_Pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_github_sum="4a9dc27587411f8eb181d12ab82b68e97a58b5fa78734fe84bc4405a0f7be21a"
_github_sig_sum="96f2a529fb8225b09704b56ff6ee69c3a023847c85ccd8256e34503f57479cd6"
_bundle_sum="b27968d1f2320d4b0db8801a1200ba8c47f620c87172847733dc9d824fffde24"
_bundle_sig_sum="98c2bd9d556d3c75912974cb3e13ea1c99ec7bf328ec791c7a02f21743445f4b"
_npm_sum=""
_npm_sig_sum=""
if [[ "${_npm}" == "true" ]]; then
  _sum="${_npm_sum}"
  _sig_sum="${_npm_sig_sum}"
elif [[ "${_npm}" == "false" ]]; then
  if [[ "${_git}" == "false" ]]; then
    _sum="${_github_sum}"
    _sig_sum="${_github_sig_sum}"
  elif [[ "${_git}" == "true" ]]; then
    _sum="${_bundle_sum}"
    _sig_sum="${_bundle_sig_sum}"
  fi
fi
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  _uri="${_evmfs_uri}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/${_pkg}/-/${_tarfile}"
  elif [[ "${_npm}" == "false" ]]; then
    _uri="${_url}/archive/${_commit}.${_archive_format}"
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

_git_unbundle() {
  local \
    _tarname="${1}" \
    _bundle \
    _repo \
    _msg=()
  _bundle="${srcdir}/${_tarname}.bundle"
  _repo="${srcdir}/${_tarname}"
  _msg=(
    "Cloning '${_bundle}' into '${_repo}'."
  )
  msg \
    "${_msg[*]}"
  git \
    clone \
      "${_bundle}" \
      "${_repo}" || \
  git \
    -C \
      "${_repo}" \
      pull || \
  true
}

prepare() {
  local \
    _bash_files=() \
    _file \
    _like \
    _os \
    _src
  _like="never-gonna-give-you-up"
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _git_unbundle \
        "${_tarname}"
    fi
  fi
}

build() {
  cd \
    "${_tarname}"
  npm \
    install
  npm \
    pack
  mv \
    "${_pkg}-${_pkgver_module}.tgz" \
    "${srcdir}"
}

package_rom-patcher() {
  local \
    _npm_options=() \
    _find_opts=()
  _npm_options=(
    -g 
    # --user 
    #   root 
    --prefix 
      "${pkgdir}/usr"
  )
  find_opts+=(
    -type
      "d"
    -exec
      chmod
        755
        '{}'
        +
  )
  npm \
    install \
    "${_npm_options[@]}" \
    "${srcdir}/${_pkg}-${_pkgver_module}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    "${_find_opts[@]}"
}


# vim:set sw=2 sts=-1 et:
