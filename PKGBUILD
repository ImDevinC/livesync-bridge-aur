# Maintainer: Devin Collins <me@imdevinc.com>

pkgname=livesync-bridge
pkgver=0.0.1
pkgrel=1
pkgdesc="Self-hosted Obsidian Livesync connector"
arch=('x86_64')
url="https://github.com/vrtmrz/livesync-bridge"
source=(
  "git+https://github.com/vrtmrz/livesync-bridge.git#branch=main"
  "livesync-bridge@.service"
)
sha256sums=(
  'SKIP'
  'SKIP'
)
options=(!strip !debug)
depends=(deno git)

package() {
  install -Dm 644 livesync-bridge@.service "${pkgdir}/usr/lib/systemd/user/livesync-bridge@.service"
  cd "${pkgname}"
  git init
  git submodule update --init --recursive

  find ./ -type f -exec install -Dm755 {} ${pkgdir}/usr/lib/livesync-bridge/{} \;
}
