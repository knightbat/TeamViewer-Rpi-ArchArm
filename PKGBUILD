# Maintainer: Jayakrishnan M <javajk2537 at gmail dot com>

pkgname=teamviewer-host-rpi
pkgver=12.0.78433
pkgrel=1
pkgdesc='TeamViewer Host for Raspberry Pi'
arch=('armv7h')
url='http://www.teamviewer.com'
license=('custom')
options=('!strip')
provides=('teamviewer-host-rpi')
depends_armv7h=(
	'fontconfig'
	'libpng12'
	'libsm'
	'libxinerama'
	'libxrender'
	'libjpeg6-turbo'
	'libxtst'
	'qt5-x11extras'
	'qt5-webkit' 
	'qt5-webview' 
	'qt5-quickcontrols' 
	'qt5-declarative'
  )
install=teamviewer-host-rpi.install

source=("https://download.teamviewer.com/download/linux/teamviewer-host_armhf.deb")
md5sums=('4b5f8f8f6b1bef428e30ee0102f908dc')

prepare() {
	tar -xf data.tar.xz
}

package() {
	# Install
	cp -dr --no-preserve=ownership {etc,opt,usr,var} "${pkgdir}"/

	# Additional files
	rm "${pkgdir}"/opt/teamviewer/tv_bin/xdg-utils/xdg-email
	install -D -m0644 "${pkgdir}"/opt/teamviewer/tv_bin/script/teamviewerd.service \
		"${pkgdir}"/usr/lib/systemd/system/teamviewerd.service
	install -d -m0755 "${pkgdir}"/usr/{share/applications,share/licenses/teamviewer}
	ln -s /opt/teamviewer/tv_bin/desktop/com.teamviewer.teamviewer-host.desktop \
		"${pkgdir}"/usr/share/applications/teamviewer.desktop
	ln -s /opt/teamviewer/License.txt \
		"${pkgdir}"/usr/share/licenses/teamviewer/LICENSE

}
