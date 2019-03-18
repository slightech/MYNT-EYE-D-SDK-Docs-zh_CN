.. _build_linux:

Linux SDK 用户指南
==================

1. 安装 SDK 依赖
----------------

1.1 安装 OpenCV
~~~~~~~~~~~~~~~

*如果您已经安装了 opencv 或者您想要使用 ROS，您可以跳过这步.*

1.1.1 apt 或者编译安装 OpenCV (选择一个)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1.1.1.1 使用 apt 安装 OpenCV (推荐)
'''''''''''''''''''''''''''''''''''

.. code-block:: bash

   sudo apt-get install libopencv-dev

1.1.1.2 编译安装 OpenCV
'''''''''''''''''''''''

   OpenCV 如何编译安装，请见官方文档
   `Installation in Linux <https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html>`__\
   。或参考如下命令：

.. code-block:: bash

   [compiler] sudo apt-get install build-essential
   [required] sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
   [optional] sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

.. code-block:: bash

   git clone https://github.com/opencv/opencv.git
   cd opencv/
   git checkout tags/3.4.5

   cd opencv/
   mkdir build
   cd build/

   cmake ..

   make -j4
   sudo make install

1.2 安装点云例程依赖的 PCL 库 (可选)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   sudo apt-get install libpcl-dev libproj-dev libopenni2-dev libopenni-dev

1.3 建立 libGL.so 软链接用以解决在 TX1/TX2 上的 bug (可选)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   sudo ln -sf /usr/lib/aarch64-linux-gnu/tegra/libGL.so /usr/lib/aarch64-linux-gnu/libGL.so

2. 编译 SDK
-----------

.. code-block:: bash

   git clone https://github.com/slightech/MYNT-EYE-D-SDK.git
   cd MYNT-EYE-D-SDK

2.1 初始化 SDK
~~~~~~~~~~~~~~

.. note::
   因为设备权限的问题，命令执行完成之后，您必须重新拔插设备(这个操作在同一台电脑上，只需要做一次)。

.. code-block:: bash

   make init

.. _编译-sdk-1:

2.2 编译 SDK
~~~~~~~~~~~~

.. code-block:: bash

   make all

3. 运行例程
-----------

.. Note::
  默认打开矫正后的图像。(跑vio时需要使用原图，跑深度或者点云使用矫正后的图像)

1) get_image 显示左目的图像和彩色深度图 (兼容USB2.0)

.. code-block:: bash

   ./samples/_output/bin/get_image

2) get_stereo_image 显示左右目的图像和彩色深度图

.. code-block:: bash

   ./samples/_output/bin/get_stereo_image

3) get_depth 显示左目的图像，16UC1的深度图和鼠标选中的像素的深度值(mm)

.. code-block:: bash

   ./samples/_output/bin/get_depth

4) get_points 显示左目的图像，16UC1的深度图和点云

.. code-block:: bash

   ./samples/_output/bin/get_points

5) get_imu 打印 imu 数据

.. code-block:: bash

   ./samples/_output/bin/get_imu

6) get_img_params 打印相机参数并保存在文件中

.. code-block:: bash

   ./samples/_output/bin/get_img_params

7) get_imu_params 打印 imu 参数并保存在文件中

.. code-block:: bash

   ./samples/_output/bin/get_imu_params

8) get_from_callbacks 使用回调方式获取图像和 imu 数据

.. code-block:: bash

   ./samples/_output/bin/get_from_callbacks

9) get_all_with_options 使用不同参数打开设备

.. code-block:: bash

   ./samples/_output/bin/get_all_with_options


4 安装带有 OpenCV 的 ROS
------------------------

如果您不使用 ROS(The Robot Operation System), 您可以跳过此部分.

4.1 安装 ROS Kinectic 版本
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   cd ~
   wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/master/ros_install.sh && \
   chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

.. note::

   ROS Kinetic 会自动安装 OpenCV, JPEG.

4.2 编译 ROS Wrapper
~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   make ros

**Core:**

.. code-block:: bash

   roscore

**RViz Display:**

.. code-block:: bash

   source ./wrappers/ros/devel/setup.bash
   roslaunch mynteye_wrapper_d display.launch

**Publish:**

.. code-block:: bash

   source ./wrappers/ros/devel/setup.bash
   roslaunch mynteye_wrapper_d mynteye.launch

**Subscribe:**

.. code-block:: bash

   source ./wrappers/ros/devel/setup.bash
   rosrun mynteye_wrapper_d mynteye_listener_d

4.3 编译内测版设备 ROS Wrapper
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   make ros

**Core:**

.. code-block:: bash

   roscore

**RViz Display:**

.. code-block:: bash

   source ./wrappers/beta_ros/devel/setup.bash
   roslaunch mynteye_wrapper_d_beta display.launch

**Publish:**

.. code-block:: bash

   source ./wrappers/beta_ros/devel/setup.bash
   roslaunch mynteye_wrapper_d_beta mynteye.launch

**Subscribe:**

.. code-block:: bash

   source ./wrappers/beta_ros/devel/setup.bash
   rosrun mynteye_wrapper_d_beta mynteye_listener_d_beta

5. 打包
-------

如果打包指定版本OpenCV的包：

.. code-block:: bash

   cd <sdk>
   make cleanall
   export OpenCV_DIR=<install prefix>

   export OpenCV_DIR=/usr/local
   export OpenCV_DIR=$HOME/opencv-2.4.13.3

Packaging:

.. code-block:: bash

   cd <sdk>  #<sdk>为SDK所在路径
   make pkg

6. 清理
-------

.. code-block:: bash

   cd <sdk>  #<sdk>为SDK所在路径
   make cleanall
   make uninstall
