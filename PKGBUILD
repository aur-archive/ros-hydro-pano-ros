# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - The ros frontend to the pano subsystem."
url='http://ros.org/wiki/pano_ros'

pkgname='ros-hydro-pano-ros'
pkgver='2.2.5'
_pkgver_patch=1
arch=('any')
pkgrel=2
license=('BSD')

ros_makedepends=(ros-hydro-message-generation
  ros-hydro-cv-bridge
  ros-hydro-rospy
  ros-hydro-sensor-msgs
  ros-hydro-image-transport
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-actionlib
  ros-hydro-pano-py
  ros-hydro-actionlib-msgs
  ros-hydro-std-msgs)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-cv-bridge
  ros-hydro-rospy
  ros-hydro-message-runtime
  ros-hydro-sensor-msgs
  ros-hydro-image-transport
  ros-hydro-roscpp
  ros-hydro-actionlib
  ros-hydro-pano-py
  ros-hydro-actionlib-msgs
  ros-hydro-std-msgs)
depends=(${ros_depends[@]})

_tag=release/hydro/pano_ros/${pkgver}-${_pkgver_patch}
_dir=pano_ros
source=("${_dir}"::"git+https://github.com/turtlebot-release/turtlebot_apps-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
