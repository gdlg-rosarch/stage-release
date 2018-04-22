# Script generated with Bloom
pkgdesc="ROS - Mobile robot simulator http://rtv.github.com/Stage"
url='http://rtv.github.com/Stage'

pkgname='ros-lunar-stage'
pkgver='4.3.0_1'
pkgrel=1
arch=('any')
license=('GPL'
)

makedepends=('cmake'
'fltk'
'gtk2'
'libjpeg-turbo'
'libtool'
'mesa'
'pkg-config'
)

depends=('fltk'
'gtk2'
'libjpeg-turbo'
'mesa'
'ros-lunar-catkin'
)

conflicts=()
replaces=()

_dir=stage
source=()
md5sums=()

prepare() {
    cp -R $startdir/stage $srcdir/stage
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

