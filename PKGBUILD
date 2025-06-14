# Maintainer: orsll <rodrigo.orselli@gmail.com>

pkgname=iosevka-custom
pkgver=33.2.5
pkgrel=1
pkgdesc="Typeface family designed for coding, terminal use and technical documents"
arch=('any')
url="https://typeof.net/Iosevka"
license=('OFL-1.1')
makedepends=('npm' 'ttfautohint')
source=(
	"https://github.com/be5invis/Iosevka/archive/refs/tags/v${pkgver}.tar.gz"
	"https://raw.githubusercontent.com/be5invis/Iosevka/v${pkgver}/LICENSE.md"
	'orsa.patch'
	'private-build-plans.toml'
)
sha256sums=(
	'3fc1f3c59ee77dec2e8bf533805da4c2a6f7e6c22c7a2e2bb1e757c858c4909c'
	'52579dd4ebbda8e5a9d314e395dbfe40de82b4b7b3007ec8458876823af8dddd'
	'161b20b135fb9b13e7cb1b6d9f59c4d7285fcb52040bbe4a323cbccd0ee9e2d4'
	'a34e4124f93c997d4095e3ed8bb0e97e7cdb163511d33ea002294163b5d8894d'
)

prepare() {
	cd "$srcdir/Iosevka-${pkgver}"
	patch -p1 -i "$srcdir/orsa.patch"
	cp "$srcdir/private-build-plans.toml" .
}

build() {
	cd "$srcdir/Iosevka-${pkgver}"
	npm install
	npm run build -- ttf::IosevkaCustom --jCmd=4
	npm run build -- ttf::IosevkaUbuntu --jCmd=4
	npm run build -- ttf::IosevkaFira   --jCmd=4
}

package() {
	cd "$srcdir/Iosevka-${pkgver}"
	install -d $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaCustom/TTF/*.ttf $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaFira/TTF/*.ttf   $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaUbuntu/TTF/*.ttf $pkgdir/usr/share/fonts/TTF/
	install -Dm644 LICENSE.md ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.md
}
