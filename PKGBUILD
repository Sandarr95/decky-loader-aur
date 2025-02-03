# Maintainer: Sander Kolman <Sandarr95@users.noreply.github.com>
pkgname=decky-loader-bin
pkgver=3.0.5
pkgrel=4
pkgdesc="Unofficial Arch build of Decky Loader, a homebrew plugin launcher for the Steam Deck."
arch=('x86_64')
url="https://github.com/SteamDeckHomebrew/decky-loader"
license=('MIT')
provides=('decky-loader')
conflicts=('decky-loader')
source=("PluginLoader::${url}/releases/download/v${pkgver}/PluginLoader"
        "decky-loader@.service::${url}/raw/v${pkgver}/dist/plugin_loader-release.service"
        "decky-loader-helper")
sha256sums=('a8b7bd58ff0c0ac80f5c07e1fa13bee45f1bb17195283f4902a7930c40aba761'
            '64d6aa626aa45e1659e3137aa3afd72edd840094199d62bb6ff2e73c5ce738b1'
            'SKIP')

build() {
    sed -i "s|\${HOMEBREW_FOLDER}|/home/%i/.local/var/opt/decky-loader|" "${srcdir}/decky-loader@.service"
    sed -i "/^ExecStart=/i ExecStartPre=/usr/bin/decky-loader-helper v${pkgver} %i" "${srcdir}/decky-loader@.service"
}

package() {
    install -Dm 644 "${srcdir}/decky-loader@.service" "${pkgdir}/usr/lib/systemd/system/decky-loader@.service"
    install -Dm 644 "${srcdir}/PluginLoader" "${pkgdir}/usr/lib/decky-loader/PluginLoader"
    install -Dm 755 "${srcdir}/decky-loader-helper" "${pkgdir}/usr/bin/decky-loader-helper"
}
