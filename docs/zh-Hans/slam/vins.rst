.. _slam_vins:

`VINS-Mono <https://github.com/HKUST-Aerial-Robotics/VINS-Mono>`_ 如何整合
============================================================================


在 MYNT® EYE 上运行 VINS-Mono，请依照这些步骤：
------------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 及 :ref:`ros_install`。
2. 按照一般步骤安装 VINS-Mono 。
3. 在 `这里 <https://github.com/slightech/MYNT-EYE-VINS-Sample/blob/mynteye/config/mynteye/mynteye_d_config.yaml>`__ 更新 ``distortion_parameters`` 和 ``projection_parameters`` 参数。
4. 运行 mynteye_wrapper_d 和 VINS-Mono 。

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
  git clone -b mynteye https://github.com/slightech/MYNT-EYE-VINS-Sample.git
  cd ..
  catkin_make
  source devel/setup.bash
  echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
  source ~/.bashrc

获取图像校准参数
----------------

使用 MYNT® EYE 的左目摄像头和 IMU 。通过 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ API的 ``GetIntrinsics()`` 函数和 ``GetExtrinsics()`` 函数，可以获得当前工作设备的图像校准参数：

.. code-block:: bash

  cd MYNT-EYE-D-SDK
  ./samples/_output/bin/get_img_params

这时，可以获得针孔模型下的 ``distortion_parameters`` 和 ``projection_parameters`` 参数，然后在 `这里 <https://github.com/slightech/MYNT-EYE-VINS-Sample/blob/mynteye/config/mynteye/mynteye_d_config.yaml>`__ 更新。


在 MYNT® EYE 上运行 VINS-Mono
-----------------------------

1.运行mynteye节点

.. code-block:: bash

  cd (local path of MYNT-EYE-D-SDK)
  source ./wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d mynteye.launch

2.打开另一个命令行运行vins

.. code-block:: bash

  cd ~/catkin_ws
  roslaunch vins_estimator mynteye_d.launch

