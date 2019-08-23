.. _slam_okvis:

`OKVIS <https://github.com/ethz-asl/okvis>`_ 如何整合
=============================================================

在 MYNT® EYE 上运行 OKVIS ，请依照这些步骤：
----------------------------------------------

1. 下载 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ 并 :ref:`sdk_install_ros`。
2. 安装依赖，按照原始 OKVIS 步骤安装 MYNT-EYE-OKVIS-Sample 。
3. 更新相机参数到 ``<OKVIS>/config/config_mynteye_d.yaml`` 。
4. 在 MYNT® EYE 上运行 OKVIS 。

.. tip::

  OKVIS暂不支持arm平台。


安装 MYNT® EYE OKVIS
---------------------

首先安装原始 OKVIS 及依赖：

.. code-block:: bash

  sudo apt-get install libgoogle-glog-dev

  git clone -b mynteye https://github.com/slightech/MYNT-EYE-OKVIS-Sample.git
  cd MYNT-EYE-OKVIS-Sample/
  mkdir build && cd build
  cmake ..
  make

获取相机校准参数
-----------------

通过 `MYNT-EYE-D-SDK <https://github.com/slightech/MYNT-EYE-D-SDK.git>`_ API 的 ``GetIntrinsics()`` 函数和 ``GetExtrinsics()`` 函数，可以获得当前工作设备的图像校准参数：

.. code-block:: bat

  cd MYNT-EYE-D-SDK
  ./samples/_output/bin/get_img_params

这时，可以获得针孔模型下的 ``distortion_parameters`` 和 ``projection_parameters`` 参数，然后在 `这里 <https://github.com/slightech/MYNT-EYE-OKVIS-Sample/blob/mynteye/config/config_mynteye_d.yaml>`_ 更新。


.. code-block:: bash

  distortion_coefficients: [coeffs]   # only first four parameters of coeffs need to be filled
  focal_length: [fx, fy]
  principal_point: [cx, cy]
  distortion_type: radialtangential

运行 MYNT® EYE OKVIS
---------------------
运行``mynteye_wrapper_d``

.. code-block:: bash

  cd MYNT-EYE-D-SDK
  source wrappers/ros/devel/setup.bash
  roslaunch mynteye_wrapper_d mynteye.launch

运行 ``MYNT-EYE-OKVIS-Sample``，打开一个新的窗口并运行以下步骤：

.. code-block:: bash

  cd MYNT-EYE-OKVIS-Sample/build
  source devel/setup.bash
  roslaunch okvis_ros mynteye_d.launch

使用 ``rviz`` 来显示：

.. code-block:: bash

  cd ~/catkin_okvis/src/MYNT-EYE-OKVIS-Sample/config
  rosrun rviz rviz -d rviz.rviz
