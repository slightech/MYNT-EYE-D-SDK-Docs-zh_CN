.. _slam_vins_fusion:

`VINS-Fusion <https://github.com/HKUST-Aerial-Robotics/Vins-Fusion>`_ 如何整合
==============================================================================


在 MYNT® EYE 上运行 VINS-Fusion，请依照这些步骤：
------------------------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 及 :ref:`sdk_install_ros`。
2. 按照步骤安装 VINS-Fusion 。
3. 运行 mynteye_wrapper_d 和 VINS-Fusion 。


快捷安装 ROS Kinetic (若已安装，请忽略)
---------------------------------------

.. code-block:: bash

  cd ~
  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/master/ros_install.sh && \
  chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic


在 docker 上运行 VINS-FUSION
---------------------------------

.. note::

  为了能够使用docker进行编译，建议使用16G以上的RAM，或者确保RAM和虚拟内存空间大于16G。

安装docker
++++++++++++

.. code-block:: bash

  sudo apt-get update
  sudo apt-get install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg-agent \
      software-properties-common
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  sudo add-apt-repository \
     "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) \
     stable"
  sudo apt-get update
  sudo apt-get install docker-ce docker-ce-cli containerd.io

.. tip::

  可以使用 ``sudo usermod -aG docker $YOUR_USER_NAME`` 添加账号到 ``docker group`` 。
  如果遇到"Permission denied"的问题，可以重启命令行或注销并重新登录。

安装 MYNT-EYE-VINS-FUSION-Samples
++++++++++++++++++++++++++++++++++++++

.. code-block::

  git clone -b docker_feat https://github.com/slightech/MYNT-EYE-VINS-FUSION-Samples.git
  cd MYNT-EYE-VINS-FUSION-Sample/docker
  make build

运行 VINS_FUSION
+++++++++++++++++++++++

1.运行mynteye节点

.. code-block:: bash

  cd MYNT-EYE-D-SDK (local path of MYNT-EYE-D-SDK)
  source ./wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d vins_fusion.launch stream_mode:=1 # stereo camera with 640x480

2.打开另一个命令行运行vins-fusion

.. code-block:: bash

  cd MYNT-EYE-VINS-FUSION-Sample/docker (local path of MYNT-EYE-VINS-FUSION-Sample)
  ./run.sh mynteye-d/mynt_mono_config.yaml  # mono+imu fusion
  # ./run.sh mynteye-d/mynt_stereo_config.yaml  # Stereo fusion
  # ./run.sh mynteye-d/mynt_stereo_imu_config.yaml # Stereo+imu fusion
