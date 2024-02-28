pkgname=decky-loader
pkgver=2.11.1
pkgrel=1
pkgdesc="Decky Loader is a homebrew plugin launcher for the Steam Deck."
arch=('x86_64')
url="https://github.com/SteamDeckHomebrew/decky-loader"
license=('MIT')
source=("PluginLoader::${url}/releases/download/v${pkgver}/PluginLoader"
	    "decky-loader@.service::${url}/raw/v${pkgver}/dist/plugin_loader-release.service"
	    "decky-loader-helper")
sha256sums=('c207bca1281d9f4e83587d6c443a74aad43caec4ec31894429afbe71d2aa2b8a'
	        '5c3b5e1493469e69ad37f177a16265a44bf675fdd5e3c002570bcf73bae618dc'
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
