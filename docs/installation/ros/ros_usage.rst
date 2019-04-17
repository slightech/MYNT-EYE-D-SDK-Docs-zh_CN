.. _ros_usage:

ROS 如何使用
============

按照 :ref:`ros_install`，编译再运行节点。

``rostopic list`` 可以列出发布的节点：

.. code-block:: bash

   /mynteye/depth/camera_info
   /mynteye/depth/image_raw
   /mynteye/depth/image_raw/compressed
   /mynteye/depth/image_raw/compressed/parameter_descriptions
   /mynteye/depth/image_raw/compressed/parameter_updates
   /mynteye/depth/image_raw/compressedDepth
   /mynteye/depth/image_raw/compressedDepth/parameter_descriptions
   /mynteye/depth/image_raw/compressedDepth/parameter_updates
   /mynteye/depth/image_raw/theora
   /mynteye/depth/image_raw/theora/parameter_descriptions
   /mynteye/depth/image_raw/theora/parameter_updates
   /mynteye/imu/data_raw
   /mynteye/imu/data_raw_processed
   /mynteye/left/camera_info
   /mynteye/left/image_color
   /mynteye/left/image_color/compressed
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
  <!-- Framerate -->
  <arg name="framerate" default="30" />

  <!--
  Device mode
    device_color: left_color ✓ right_color ? depth x
    device_depth: left_color x right_color x depth ✓
    device_all:   left_color ✓ right_color ? depth ✓
  Note: ✓: available, x: unavailable, ?: depends on #stream_mode
  -->
  <arg name="dev_mode" default="$(arg device_all)" />

  <arg name="color_mode" default="$(arg color_raw)" />
  <!-- Note: must set DEPTH_RAW to get raw depth values for points -->
  <arg name="depth_mode" default="$(arg depth_raw)" />
  <arg name="stream_mode" default="$(arg stream_2560x720)" />

  <!-- Auto-exposure -->
  <arg name="state_ae" default="true" />
  <!-- Auto-white balance -->
  <arg name="state_awb" default="true" />
  <!-- IR intensity -->
  <arg name="ir_intensity" default="4" />
  <!-- IR Depth Only -->
  <arg name="ir_depth_only" default="false" />

  <!-- Setup your local gravity here -->
  <arg name="gravity" default="9.8" />
