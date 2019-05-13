.. _camera_control_params:

相机控制参数API
===============

打开或关闭自动曝光
------------------

.. code-block:: c++

   /** Auto-exposure enabled or not  default enabled*/
   bool AutoExposureControl(bool enable);    see "camera.h"

打开或关闭自动白平衡
--------------------

.. code-block:: c++

   /** Auto-white-balance enabled or not  default enabled*/
   bool AutoWhiteBalanceControl(bool enable);    see "camera.h"

设置 IR 强度
------------

.. code-block:: c++

   /** set infrared(IR) intensity [0, 10] default 4*/
   void SetIRIntensity(const std::uint16_t &value);     see "camera.h"

设置全局增益
------------

.. note::
 需要在相机打开后关闭自动曝光

.. code-block:: c++

   /** Set global gain [1 - 16]
    * value -- global gain value
    * */
   void SetGlobalGain(const float &value);    see "camera.h"

设置曝光时间
------------

.. note::
 需要在相机打开后关闭自动曝光

.. code-block:: c++

   /** Recommended exposure time [1ms - 2000ms]
    * value -- exposure time value
    * */
   void SetExposureTime(const float &value);    see "camera.h"

参考代码：

.. code-block:: c++

  cam.Open(params);
  cam.AutoExposureControl(false);
  cam.SetGlobalGain(1);
  cam.SetExposureTime(0.3);

.. note::
  更改参数后需要在sdk的目录下运行

  .. code-block:: bash

    make samples

  来使设置的参数生效。