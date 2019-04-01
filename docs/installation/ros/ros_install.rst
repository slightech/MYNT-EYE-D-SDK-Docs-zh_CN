.. _ros_install:

ROS 安装
========

1.1 安装 ROS Kinectic 版本
--------------------------

.. code-block:: bash

   cd ~
   wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/master/ros_install.sh && \
   chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

..

   ROS Kinetic 会自动安装 OpenCV, JPEG.

1.2 编译 ROS Wrapper
--------------------

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
