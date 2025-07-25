# Maintainer: orsll <rodrigo.orselli@gmail.com>

pkgname=iosevka-custom
pkgver=33.2.7
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
	'ce176e4d7b7c0ac49210911af3c5216cf65113ca15082d9ec89110ed6cb7b62f'
	'52579dd4ebbda8e5a9d314e395dbfe40de82b4b7b3007ec8458876823af8dddd'
	'161b20b135fb9b13e7cb1b6d9f59c4d7285fcb52040bbe4a323cbccd0ee9e2d4'
	'87d07fbc561dc38cfd6471a021d0e1d05eddeb1b72a358e8321ed3f732f43372'
)

prepare() {
	cd "$srcdir/Iosevka-${pkgver}"
	patch -p1 -i "$srcdir/orsa.patch"
	cp "$srcdir/private-build-plans.toml" .
}

build() {
	cd "$srcdir/Iosevka-${pkgver}"
	npm install
	npm run build -- ttf::IosevkaCustom --jCmd=7
	npm run build -- ttf::IosevkaUbuntu --jCmd=7
	npm run build -- ttf::IosevkaFira   --jCmd=7
}

package() {
	cd "$srcdir/Iosevka-${pkgver}"
	install -d $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaCustom/TTF/*.ttf $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaFira/TTF/*.ttf   $pkgdir/usr/share/fonts/TTF/
	install -m644 $srcdir/Iosevka-${pkgver}/dist/IosevkaUbuntu/TTF/*.ttf $pkgdir/usr/share/fonts/TTF/
	install -Dm644 LICENSE.md ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.md
}
