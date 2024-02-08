pkgname=decky-loader
pkgver=2.10.14
pkgrel=1
pkgdesc="Decky Loader is a homebrew plugin launcher for the Steam Deck."
arch=('x86_64')
url="https://github.com/SteamDeckHomebrew/decky-loader"
license=('MIT')
source=("PluginLoader::${url}/releases/download/v${pkgver}/PluginLoader"
	    "decky-loader@.service::${url}/raw/v${pkgver}/dist/plugin_loader-release.service"
	    "decky-loader-helper")
sha256sums=('453daf99794d90ff5f0c804f8bfe846aa149ed50a18f74a3da0842570dba0b70'
	        '5c3b5e1493469e69ad37f177a16265a44bf675fdd5e3c002570bcf73bae618dc'
	        'SKIP')

build() {
    sed -i "s|\${HOMEBREW_FOLDER}|/home/%i/.local/var/opt/decky-loader|" "${srcdir}/decky-loader@.service"
	sed -i "/^ExecStart=/i ExecStartPre=/usr/bin/decky-loader-helper %i" "${srcdir}/decky-loader@.service"
}

package() {
	install -Dm 644 "${srcdir}/decky-loader@.service" "${pkgdir}/usr/lib/systemd/system/decky-loader@.service"
	install -Dm 644 "${srcdir}/PluginLoader" "${pkgdir}/usr/lib/decky-loader/PluginLoader"
	install -Dm 755 "${srcdir}/decky-loader-helper" "${pkgdir}/usr/bin/decky-loader-helper"
}
