.. _save_all_infos:

保存设备信息和参数
==================

SDK 提供了保存信息和参数的工具 ``save_all_infos`` 。

参考运行命令：

.. code-block:: bash

   ./tools/_output/bin/writer/save_all_infos

.. code-block:: bat

   # Windows
   .\tools\_output\bin\writer\save_all_infos.bat

参考运行结果，于 Linux 上：

.. code-block:: bash

   I/eSPDI_API: eSPDI: EtronDI_Init
   Device descriptors:
     name: MYNT-EYE-D1000
     serial_number: 203837533548500F002F0028
     firmware_version: 1.0
     hardware_version: 2.0
     spec_version: 1.0
     lens_type: 0000
     imu_type: 0000
     nominal_baseline: 120

默认会保存进 ``<workdir>/config``
目录。你也可以加参数，指定保存到其他目录。

保存内容如下：

::

   <workdir>/
   └─config/
      └─SN0610243700090720/
         ├─device.info
         └─imu.params

完整代码样例
`save_all_infos.cc <https://github.com/slightech/MYNT-EYE-D-SDK/blob/master/tools/writer/save_all_infos.cc>`__
。
