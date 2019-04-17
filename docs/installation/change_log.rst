.. _change_log:


SDK 更新日志
===============

2019-04-17 v1.7.5
-------------------

1. 移除了 beta_ros wrapper。

2. 为内侧版的相机增加了默认的 camera info。

3. 增加了点云查看ply文件的样例。

4. ros wrapper中增加了slam相关的launch。

5. 修复了 ros display中颜色异常问题。

6. 修复了 ros display 点云抖动问题。


2019-03-25 v1.7.4
-----------------

1、修复了ros camera info 不同设备兼容问题。

2、修复了 Ubuntu18.04 特定 opencv 版本编译问题。


2019-03-18 v1.7.3
-----------------

1、增加对外部传感器（超声波传感器，GPS）的支持。

2、depth与color图根据frame id同步。

3、增加兼容USB2.0的范例。

4、修复ROS下左右目发布camera info帧率为正常值两倍的问题。

5、文档优化。