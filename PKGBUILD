# Maintainer: Chris <christopher.r.mullins g-mail>
# Contributor: cornholio <vigo.the.unholy.carpathian@gmail.com>
pkgname=afni
pkgver=16.1.27
pkgrel=1
pkgdesc="An open-source environment for processing and displaying functional MRI data"
arch=("i686" "x86_64")
url="http://afni.nimh.nih.gov"
license=(custom)
depends=("tcsh" "python" "gcc-libs" "gsl" "libxpm" "glu" "lesstif" "libjpeg-turbo" "libxmu" "libxft")
source=('http://afni.nimh.nih.gov/pub/dist/tgz/afni_src.tgz' 'Makefile.patch')
sha512sums=('d8b652afd226e5b6f8ca4d877cad6b9d2e7e94553e203500eda3928a9052471e65000109068c657e6a13137e46854a41112479a7b339e36a271a4cd636e73d6e'
            '71bc8a4838af3f33a9b789d704ec578bafea24066592af89463d3aa270cd02782c9bd1461173c738990340a6c3af6deeef422c3c08830934d215cce865068c44')


prepare() {
  cd "${srcdir}"/afni_src
  cp Makefile.linux_openmp_64 Makefile
  patch -Np0 -i ../Makefile.patch
}

build() {	
  cd ${srcdir}/afni_src
  MAKEFLAGS="" CPPFLAGS="" make vastness
}

package(){
  cd ${srcdir}/afni_src
  make install
  mkdir -p $pkgdir/opt
  cp -r $srcdir/build $pkgdir/opt/afni
  find $pkgdir/opt/afni -name \*.a -delete
  find $pkgdir/opt/afni -name \*.h -delete
  mkdir -p $pkgdir/usr/share/licenses/afni
  cp $srcdir/afni_src/README.copyright $pkgdir/usr/share/licenses/afni/LICENSE
}
