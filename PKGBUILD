pkgname=blender-retopology-polystrips
pkgver=1.0.2
pkgrel=1
pkgdesc="CG Cookie Polystrips Retopology Tool for Blender"
arch=(any)
url="https://github.com/CGCookie/retopology-polystrips"
license=("GPL v2")
source=("polystrips.tar.gz::https://github.com/CGCookie/retopology-polystrips/archive/v${pkgver//_/-}.tar.gz"
"lib.tar.gz::https://github.com/CGCookie/retopology-lib/archive/1.0.1.tar.gz")
depends=("blender>=15:2.72b")
makedepends=(python)
md5sums=('3c7a16c2ec3de4449dba59f661027451'
         'b020e0dffe5a893621163866e958541f')

_blender_version=`blender -v | grep "Blender\s" | awk '{print $2}'`

package() {
	cd "$srcdir/retopology-polystrips-${pkgver//_/-}"
	find . -name '*.py' -exec install -Dm755 {} "$pkgdir/usr/share/blender/${_blender_version}/scripts/addons/retopology-polystrips/"{} \;
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/blender-retopology-polystrips/LICENSE"
	cd ../retopology-lib-1.0.1
	find . -name '*.py' -exec install -Dm755 {} "$pkgdir/usr/share/blender/${_blender_version}/scripts/addons/retopology-polystrips/lib/"{} \;
	python -m compileall "$pkgdir/usr/share/blender"
}
