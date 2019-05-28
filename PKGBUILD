pkgname=python-weechat-matrix
pkgver=r634.bdab5c8
pkgrel=0.1
pkgdesc="Python3/2 plugin for Weechat to communicate over the Matrix protocol"
arch=('x86_64')
url="https://github.com/poljar/weechat-matrix"
license=('The Unlicense')
groups=()
makedepends=('git' 'libolm')
provides=('python-weechat-matrix' 'python2-weechat-matrix')
conflicts=('python2-weechat-matrix' 'python-weechat-matrix')
source=('weechat-matrix::git+https://github.com/poljar/weechat-matrix.git')
md5sums=('SKIP')

pkgver() {
    cd "${srcdir}/weechat-matrix"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package_python-weechat-matrix() {
	makedepends=('python' 'python-pip' 'python-setuptools')
	depends=('weechat-python3-git' 
	'python-peewee' 'python-webcolors' 'python-atomicwrites' 'python-attrs'
	'python-logbook' 'python-pygments' 'libolm' 'python-olm' 'python-nio')

    cd "${srcdir}/weechat-matrix"
	
    # Install plugin scripts
    pip3 install -r requirements.txt
    make WEECHAT_HOME="${pkgdir}/usr/lib/weechat" install

    # Install License
    install -D -m 644 'LICENSE' \
        "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

package_python2-weechat-matrix() {
	makedepends=('python2' 'python2-pip' 'python2-setuptools' 'cython2')
	depends=('weechat' 'python2-atomicwrites' 'python2-pip' 'python2-attrs' 
	'python2-future' 'python2-h11' 'python2-h2' 'python2-jsonschema'  'python2-logbook'
    'python2-nio' 'python2-olm' 'python2-peewee' 'python2-pygments' 'libolm'
    'python2-pyopenssl' 'python2-typing' 'python2-unpaddedbase64' 'python2-olm'
    'python2-webcolors')
    cd "${srcdir}/weechat-matrix"

    # Install plugin scripts
    pip2 install -r requirements.txt
    make WEECHAT_HOME="${pkgdir}/usr/lib/weechat" install

    # Install License
    install -D -m 644 'LICENSE' \
        "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
