.. _update_hid_firmware:

升级协处理芯片
=================

获取协处理芯片固件
-----------------

最新固件： mynteye-d-hid-firmware-1.2.bin `Google
Drive <https://drive.google.com/open?id=1gAbTf6W10a8iwT7L9TceMVgxQCWKnEsx>`__,
`百度网盘 <https://pan.baidu.com/s/1sZKxugg5P8Dk5QgneA9ttw>`__

编译 SDK 工具
-------------

.. code-block:: bash

   cd <sdk>  #<sdk>为sdk所在路径
   make tools

升级固件
--------

.. code-block:: bash

   ./tools/_output/bin/writer/device_hid_update <firmware-file-path>
