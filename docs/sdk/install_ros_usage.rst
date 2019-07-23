.. _sdk_install_ros_usage:

ROS Wrapper 说明
================

按照 :ref:`sdk_install_ros`，编译再运行节点。

``rostopic list`` 可以列出发布的节点：

.. code-block:: bash

   /mynteye/depth/image_raw     # 深度数据
   /mynteye/imu/data_raw        # imu数据
   /mynteye/imu/data_raw_processed     # 经过处理后的imu数据
   /mynteye/left/image_mono     # 左目黑白图像
   /mynteye/left/image_color    # 左目彩色图像
   /mynteye/right/image_mono    # 右目黑白图像
   /mynteye/right/image_color   # 右目彩色图像
   /mynteye/points/data_raw     # 点云数据
   /mynteye/temp/data_raw       # imu温度数据
   ...

``rostopic hz <topic>`` 可以检查是否有数据：

.. code-block:: bash

   subscribed to [/mynteye/imu/data_raw]
   average rate: 202.806
       min: 0.000s max: 0.021s std dev: 0.00819s window: 174
   average rate: 201.167
       min: 0.000s max: 0.021s std dev: 0.00819s window: 374
   average rate: 200.599
       min: 0.000s max: 0.021s std dev: 0.00819s window: 574
   average rate: 200.461
       min: 0.000s max: 0.021s std dev: 0.00818s window: 774
   average rate: 200.310
       min: 0.000s max: 0.021s std dev: 0.00818s window: 974
     ...

``rostopic echo <topic>`` 可以打印发布数据等。了解更多，请阅读
`rostopic <http://wiki.ros.org/rostopic>`__ 。

ROS 封装的文件结构，如下所示：

::

   <sdk>/wrappers/ros/
   ├─src/
     └─mynteye_wrapper_d/
        ├─launch/
        │  ├─display.launch
        │  └─mynteye.launch
        │  └─slam
        │     ├─orb_slam2.launch
        │     └─vins_fusion.launch
        │     └─vins_mono.launch
        ├─msg/
        ├─rviz/
        ├─src/
        │  ├─mynteye_listener.cc
        │  └─mynteye_wrapper_nodelet.cc
        │  └─mynteye_wrapper_node.cc
        │  └─pointcloud_generatort.cc
        │  └─pointcloud_generator.h
        ├─CMakeLists.txt
        ├─nodelet_plugins.xml
        └─package.xml

其中 ``mynteye.launch`` 里，可以配置发布的 topics 与 frame_ids
、决定启用哪些数据、以及设定控制选项。修改分辨率和帧率需要根据 :ref:`support_resolutions`。其中，\ ``gravity``
请配置成当地重力加速度。

.. code-block:: c++

  <!-- Camera Params -->

  <!-- Device index -->
  <arg name="dev_index" default="0" />
  <!-- 修改帧率 -->
  <arg name="framerate" default="30" />

  <!--
  设置设备模式
    device_color: left_color ✓ right_color ? depth x
    device_depth: left_color x right_color x depth ✓
    device_all:   left_color ✓ right_color ? depth ✓
  Note: ✓: available, x: unavailable, ?: depends on #stream_mode
  -->
  <arg name="dev_mode" default="$(arg device_all)" />

  <!-- 设置深度模式 -->
  <!-- Note: must set DEPTH_RAW to get raw depth values for points -->
  <arg name="depth_mode" default="$(arg depth_raw)" />
  <!--
  设置分辨率
  可以设置的分辨率为 stream_640x480,stream_1280x720,stream_1280x480,stream_2560x720
  -->
  <arg name="stream_mode" default="$(arg stream_2560x720)" />

  <!-- 设置图像模式，可设置为 color_raw(原图), color_rectified(纠正图)-->
  <arg name="color_mode" default="$(arg color_raw)" />

  <!-- 设置自动曝光 -->
  <arg name="state_ae" default="true" />
  <!-- 设置自动白平衡 -->
  <arg name="state_awb" default="true" />
  <!-- 设置IR数值 -->
  <arg name="ir_intensity" default="4" />
  <!-- 设置IR Depth Only模式 -->
  <arg name="ir_depth_only" default="false" />

  <!-- Setup your local gravity here -->
  <arg name="gravity" default="9.8" />
