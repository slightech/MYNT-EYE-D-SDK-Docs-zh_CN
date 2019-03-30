.. _slam_vins_fusion:

`VINS-Fusion <https://github.com/HKUST-Aerial-Robotics/Vins-Fusion>`_ 如何整合
==============================================================================


在 MYNT® EYE 上运行 VINS-Fusion，请依照这些步骤：
------------------------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 及 :ref:`ros_install`。
2. 按照一般步骤安装 VINS-Fusion 。
3. 运行 mynteye_wrapper_d 和 VINS-Fusion 。


准备步骤
--------

1. 安装 Ubuntu 64位 16.04/18.04. ROS Kinetic/Melodic(如果已经安装ROS可以跳过). `ROS安装步骤 <http://wiki.ros.org/ROS/Installation>`_
2. 安装 `Ceres <http://ceres-solver.org/installation.html>`_


安装 MYNT-EYE-VINS-FUSION-Samples
---------------------------------

.. code-block:: bash

  mkdir -p ~/catkin_ws/src
  cd ~/catkin_ws/src
  git clone -b mynteye https://github.com/slightech/MYNT-EYE-VINS-FUSION-Samples.git
  cd ..
  catkin_make
  source ~/catkin_ws/devel/setup.bash

(如果安装失败，请尝试换一台系统干净的电脑或者重新安装系统与ROS)

在 MYNT® EYE 上运行 VINS-FUSION
-------------------------------

1.运行mynteye节点

.. code-block:: bash

  cd (local path of MYNT-EYE-D-SDK)
  source ./wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d vins_fusion.launch

2.打开另一个命令行运行vins

.. code-block:: bash

  cd ~/catkin_ws
  roslaunch vins mynteye-d-mono-imu.launch  # mono+imu fusion
  # roslaunch vins mynteye-d-stereo.launch  # Stereo fusion / Stereo+imu fusion