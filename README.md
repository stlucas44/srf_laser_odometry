# srf_laser_odometry

**Robust Planar Odometry Based on Symmetric Range Flow and Multi-Scan Alignment**

This pkgs offers a fast and reliable estimation of 2D odometry based on planar laser scans.

SRF is the continuation of [RF2O](https://github.com/MAPIRlab/rf2o_laser_odometry), a fast and precise method to
estimate the planar motion of a lidar from consecutive range scans. SRF presents a dense method for estimating planar
motion with a laser scanner. Starting from a symmetric representation of geometric consistency between scans, we derive
a precise range flow constraint and express the motion of the scan observations as a function of the rigid motion of the
scanner. In contrast to existing techniques, which align the incoming scan with either the previous one or the last
selected keyscan, we propose a combined and efficient formulation to jointly align all these three scans at every
iteration. This new formulation preserves the advantages of keyscan-based strategies but is more robust against
suboptimal selection of keyscans and the presence of moving objects.

An extensive evaluation of this method is presented with simulated and real data in both static and dynamic
environments [Journal Article](http://mapir.isa.uma.es/work/SRF-Odometry). Results show that our approach is one order
of magnitude faster and significantly more accurate than existing methods in all the conducted experiments. With a
runtime of about one~millisecond, it is suitable for those robotic applications that require planar odometry with low
computational cost.

For a full description of the algorithm, please refer to:

- M. Jaimez, J. Monroy, M. Lopez-Antequera, J. Gonzalez-Jimenez,
  **Robust Planar Odometry based on Symmetric Range Flow and Multi-Scan Alignment**. *IEEE Transactions on Robotics, pp.
  1623--1635, 2018* [SRF paper](http://mapir.isa.uma.es/work/SRF-Odometry)

# Setup:

Installation

```
# apt libs
apt update
apt install dialog apt-utils ros-$ROS_DISTRO-mrpt2

# required components
git clone git@github.com:mrpt-ros-pkg/mrpt_msgs.git
git clone -b ros1 git@github.com:mrpt-ros-pkg/mrpt_navigation.git
git clone git@github.com:tuw-robotics/marker_msgs.git

# build:
catkin build srf_laser_odometry 
```

Tested version compatibility (latest run with):

* `git@github.com:stlucas44/srf_laser_odometry.git`
    * commit: `96859cef078efc839dfe66df9cd8627edb9b93ab`
    * branch: `feature/service`
* `git@github.com:mrpt-ros-pkg/mrpt_msgs.git`
    * commit: `55ba56363d0f8da84a588b149b3459704f08b0e1`
    * branch: `master`
* `git@github.com:mrpt-ros-pkg/mrpt_navigation.git`
    * commit:`72cf6fa30f7c5ed415746b7c1fe6a97f56674858`
    * branch: `ros1`
* `git@github.com:tuw-robotics/marker_msgs.git`
    * commit: `c7ead955cf1c37d9f17ab53eaf101b769f772636`
    * branch: `master`

# Dependencies

The code provided in this repo depends on the famous Mobile Robot Programming Toolkit [MRPT](https://www.mrpt.org/). To
avoid problems with versions, we used the defatult binary version (1.3.2-1) available in the official Ubuntu
repository (`sudo apt-get install libmrpt-dev mrpt-apps`), and the ROS-pkg **mrpt_msgs_bridge** to convert data types
between MRPT and ROS.
