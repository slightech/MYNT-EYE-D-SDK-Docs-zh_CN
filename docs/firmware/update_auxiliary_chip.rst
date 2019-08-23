.. _fw_update_auxiliary_chip:

升级协处理芯片固件
======================

获取协处理芯片固件
----------------------

最新固件： MYNTEYE-D-auxiliary-chip-1.4.2.bin `Google
Drive <https://drive.google.com/open?id=1gAbTf6W10a8iwT7L9TceMVgxQCWKnEsx>`__,
`百度网盘 <https://pan.baidu.com/s/1sZKxugg5P8Dk5QgneA9ttw>`__

编译 SDK 工具
-------------

.. code-block:: bash

   cd <sdk>  # <sdk>为SDK所在路径
   make tools

升级固件
--------

.. code-block:: bash

   ./tools/_output/bin/writer/auxiliary_firmware_update <firmware-file-path>
