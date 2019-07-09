.. _slam_vins:

`VINS-Mono <https://github.com/HKUST-Aerial-Robotics/VINS-Mono>`_ 如何整合
============================================================================


在 MYNT® EYE 上运行 VINS-Mono，请依照这些步骤：
------------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 及 :ref:`ros_install`。
2. 按照步骤安装 VINS-Mono 。
3. 运行 mynteye_wrapper_d 和 VINS-Mono 。

快捷安装 ROS Kinetic (若已安装，请忽略)
---------------------------------------

.. code-block:: bash

  cd ~
  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/master/ros_install.sh && \
  chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic


在 docker 上运行 VINS-MONO
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

安装 MYNT-EYE-VINS-Samples
++++++++++++++++++++++++++++++++++++++

.. code-block::

  git clone -b docker_feat https://github.com/slightech/MYNT-EYE-VINS-Sample.git
  cd MYNT-EYE-VINS-Sample/docker
  make build

运行 VINS-MONO
+++++++++++++++++++++++

1.运行mynteye节点

.. code-block:: bash

  cd MYNT-EYE-D-SDK (local path of MYNT-EYE-D-SDK)
  source ./wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d vins_mono.launch stream_mode:=0

2.打开另一个命令行运行vins-mono

.. code-block:: bash

  cd MYNT-EYE-VINS-Sample/docker (local path of MYNT-EYE-VINS-Sample)
  ./run.sh mynteye_d.launch
