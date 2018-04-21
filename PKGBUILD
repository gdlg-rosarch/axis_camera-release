# Script generated with Bloom
pkgdesc="ROS - Python ROS drivers for accessing an Axis camera's MJPG stream. Also provides control for PTZ cameras."
url='http://ros.org/wiki/axis_camera'

pkgname='ros-kinetic-axis-camera'
pkgver='0.2.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-camera-info-manager-py'
'ros-kinetic-catkin'
'ros-kinetic-dynamic-reconfigure'
'ros-kinetic-geometry-msgs'
'ros-kinetic-message-generation'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-tf'
)

depends=('ros-kinetic-camera-info-manager-py'
'ros-kinetic-dynamic-reconfigure'
'ros-kinetic-geometry-msgs'
'ros-kinetic-message-runtime'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-tf'
)

conflicts=()
replaces=()

_dir=axis_camera
source=()
md5sums=()

prepare() {
    cp -R $startdir/axis_camera $srcdir/axis_camera
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
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

