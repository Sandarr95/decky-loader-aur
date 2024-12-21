pkgname=decky-loader
pkgver=3.0.4
pkgrel=1
pkgdesc="Decky Loader is a homebrew plugin launcher for the Steam Deck."
arch=('x86_64')
url="https://github.com/SteamDeckHomebrew/decky-loader"
license=('MIT')
source=("PluginLoader::${url}/releases/download/v${pkgver}/PluginLoader"
	    "decky-loader@.service::${url}/raw/v${pkgver}/dist/plugin_loader-release.service"
	    "decky-loader-helper")
sha256sums=('f78a502ff7e6a40a4ffacba4bb86bfabb9d34dfff3a95693e6b6d5a3010560f6'
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
