# Maintainer: Alex Taber <aft dot pokemon at gmail dot com>

pkgname=teamviewer-rpi
pkgver=11.0.63329
pkgrel=1
pkgdesc='TeamViewer Host for Raspberry Pi'
arch=('armv7h')
url='http://www.teamviewer.com'
license=('custom')
options=('!strip')
provides=('teamviewer-rpi')
depends_armv7h=(
	'fontconfig'
	'libpng12'
	'libsm'
	'libxinerama'
	'libxrender'
	'libjpeg6-turbo'
  'libxtst')
install=teamviewer-rpi.install

source=("https://download.teamviewer.com/download/linux/version_11x/teamviewer-host_armhf.deb")
md5sums=('77e9bcf2874090bf2288dacf6b6cb901')

prepare() {
	tar -xf data.tar.bz2
}

package() {
	# Install
	cp -dr --no-preserve=ownership {etc,opt,usr,var} "${pkgdir}"/

	# Additional files
	rm "${pkgdir}"/opt/teamviewer/tv_bin/xdg-utils/xdg-email
	install -D -m0644 "${pkgdir}"/opt/teamviewer/tv_bin/script/teamviewerd.service \
		"${pkgdir}"/usr/lib/systemd/system/teamviewerd.service
	install -d -m0755 "${pkgdir}"/usr/{share/applications,share/licenses/teamviewer}
	ln -s /opt/teamviewer/tv_bin/desktop/teamviewer.desktop \
		"${pkgdir}"/usr/share/applications/teamviewer.desktop
	ln -s /opt/teamviewer/License.txt \
		"${pkgdir}"/usr/share/licenses/teamviewer/LICENSE
}
