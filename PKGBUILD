# Script generated with create_pkgbuild.py
# For more information: https://github.com/ros-melodic-arch/ros-build-tools-py3
pkgdesc="ROS - Message and service definitions for interacting with Universal Robots robot controllers."
url='http://www.ros.org/'

pkgname='ros-melodic-ur-msgs'
pkgver='1.3.2'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD-3-Clause')

ros_makedepends=(
  ros-melodic-message-generation
  ros-melodic-geometry-msgs
  ros-melodic-std-msgs
  ros-melodic-catkin
)

makedepends=(
  'cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
)

ros_depends=(
  ros-melodic-std-msgs
  ros-melodic-geometry-msgs
  ros-melodic-message-runtime
)

depends=(
  ${ros_depends[@]}
)

_dir="ur_msgs-release-release-melodic-ur_msgs"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-industrial-release/ur_msgs-release/archive/release/melodic/ur_msgs/${pkgver}.tar.gz")
sha256sums=('019a4b09ff08b6ad898e89ade7cc58a6d71107993a1a693b409c99375883279e')


build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCATKIN_BUILD_BINARY_PACKAGE=ON \
    -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
    -DPYTHON_EXECUTABLE=/usr/bin/python3 \
    -DPYTHON_INCLUDE_DIR=/usr/include/python3.8 \
    -DPYTHON_LIBRARY=/usr/lib/libpython3.8.so \
    -DPYTHON_BASENAME=.cpython-38 \
    -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
