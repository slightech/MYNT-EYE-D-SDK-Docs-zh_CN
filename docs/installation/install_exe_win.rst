.. role:: raw-latex(raw)
   :format: latex
..

.. _install_exe_win:

Windows 预编译 exe 安装
=======================

   下载地址： mynteye-d-x.x.x-win-x64-opencv-3.4.3.exe `Google
   Drive <https://drive.google.com/open?id=1FQrRdpK51U43ihX5pVkMRUedtOOc0FNg>`__,
   `百度网盘 <https://pan.baidu.com/s/1GeeZ-4-DVyZJ2wUh0aknjQ>`__

安装完 SDK 的 exe 安装包后，桌面会生成 SDK 根目录的快捷方式。

进入 “\bin\samples” 目录，双击 “get_image.exe”
运行，即可看到相机画面。

.. note::

  如果无法运行样例，请先检查一下系统变量PATH中是否成功添加了 ``<SDK_ROOT_DIR>\bin`` , ``<SDK_ROOT_DIR>\bin\3rdparty`` ,
  ``<SDK_ROOT_DIR>\3rdparty\opencv\build\x64\vc15\bin`` , ``<SDK_ROOT_DIR>\3rdparty\libjpeg-turbo64\bin`` 。


生成样例工程
------------

首先，安装好 Visual Studio 2017 https://visualstudio.microsoft.com/ 和
CMake https://cmake.org/ 。

接着，进入 “\samples`” 目录， 双击 “generate.bat”
即可生成样例工程 ``_build\mynteye_samples.sln`` 。

.. tip::

  运行样例需要先右键样例，设为启动项目，然后使用Release x64运行。


