.. _sdk_install_ubuntu_src:

Ubuntu 源码安装
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

.. tip::

    如果需要安装ros，可以跳过这一步骤，直接使用ros中自带的opencv。


OpenCV 如何编译安装，请见官方文档 `Installation in Linux <https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html>`__ 。或参考如下命令：

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

    PCL安装，请见官方文档 `PCL Installation <http://www.pointclouds.org/documentation/tutorials/compiling_pcl_posix.php>`__ 。

.. tip::

    如果需要安装ros，可以跳过这一步骤，直接使用ros中自带的pcl。

.. note::

   源码编译pcl需要安装依赖Eigen,Boost,FLANN,VTK。

.. code-block:: bash

  git clone https://github.com/PointCloudLibrary/pcl.git
  cd pcl
  git checkout pcl-1.7.2
  mkdir build && cd build

  cmake -DCMAKE_BUILD_TYPE=Release ..

  make -j2
  sudo make -j2 install

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

10) get_depth_with_filter 显示滤波后的深度图像

.. code-block:: bash

  ./samples/_output/bin/get_depth_with_filter

11) get_points_with_filter 显示滤波后的点云图像

.. code-block:: bash

  ./samples/_output/bin/get_points_with_filter

4 安装带有 OpenCV 的 ROS
------------------------

如果您不使用 ROS(The Robot Operation System), 您可以跳过此部分。

ROS安装与运行步骤，参考 :ref:`sdk_install_ros` 以及 :ref:`sdk_install_ros_usage` 。


5. 打包
-------

如果打包指定版本OpenCV的包：

.. code-block:: bash

   cd <sdk>  # <sdk>为SDK所在路径
   make cleanall
   export OpenCV_DIR=<install prefix>

   export OpenCV_DIR=/usr/local
   export OpenCV_DIR=$HOME/opencv-2.4.13.3

Packaging:

.. code-block:: bash

   cd <sdk>  # <sdk>为SDK所在路径
   make pkg

6. 清理
-------

.. code-block:: bash

   cd <sdk>  # <sdk>为SDK所在路径
   make cleanall
   make uninstall
