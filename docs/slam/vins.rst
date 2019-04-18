.. _slam_vins:

`VINS-Mono <https://github.com/HKUST-Aerial-Robotics/VINS-Mono>`_ 如何整合
============================================================================


在 MYNT® EYE 上运行 VINS-Mono，请依照这些步骤：
------------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 及 :ref:`ros_install`。
2. 按照一般步骤安装 VINS-Mono 。
3. 运行 mynteye_wrapper_d 和 VINS-Mono 。

快捷安装 ROS Kinetic (若已安装，请忽略)
---------------------------------------

.. code-block:: bash

  cd ~
  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/master/ros_install.sh && \
  chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

安装 MYNT-EYE-VINS-Sample
--------------------------

.. code-block:: bash

  mkdir -p ~/catkin_ws/src
  cd ~/catkin_ws/src
  git clone https://github.com/slightech/MYNT-EYE-VINS-Sample.git
  cd ..
  catkin_make
  source devel/setup.bash
  echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
  source ~/.bashrc


在 MYNT® EYE 上运行 VINS-Mono
-----------------------------

1.运行mynteye节点

.. code-block:: bash

  cd (local path of MYNT-EYE-D-SDK)
  source ./wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d vins_mono.launch

2.打开另一个命令行运行vins

.. code-block:: bash

  cd ~/catkin_ws
  roslaunch vins_estimator mynteye_d.launch

