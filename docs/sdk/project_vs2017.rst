.. _project_vs2017:

Visual Studio 2017 如何使用 SDK
===============================

本教程将使用 Visual Studio 2017 创建一个项目来使用 SDK 。

   你可以在 ``<sdk>/platforms/projects/vs2017`` 目录下找到工程样例。

准备
----

-  Windows: 安装 SDK 的 exe 包

创建项目
--------

打开 Visual Studio 2017 ，然后 ``File > New > Project``\ ，

.. image:: ../static/images/projects/vs2017/1_new_pro.png

选择 “Windows Console Application” ，设置项目位置和名字，点击 “OK”，

.. image:: ../static/images/projects/vs2017/2_new_pro.png

最后，你可以看到一个新的项目被创建，

.. image:: ../static/images/projects/vs2017/3_new_pro.png

配置项目
--------

右键点击该项目， 打开 “Properties” 窗口，

.. image:: ../static/images/projects/vs2017/4_config.png

将 “Configuration” 更改为 “All Configurations” ，然后添加以下路径到
“Additional Include Directories” ，

.. code:: bash

   $(MYNTEYED_SDK_ROOT)\include
   $(MYNTEYED_SDK_ROOT)\3rdparty\opencv\build\include

.. image:: ../static/images/projects/vs2017/5_config_include.png

添加以下定义到 “Preprocessor Definitions”,

.. code:: bash

   WITH_OPENCV
   WITH_OPENCV3

..  image:: ../static/images/projects/vs2017/6_config_definition.png

添加以下路径到 “Additional Library Directories” ，

.. code:: bash

   $(MYNTEYED_SDK_ROOT)\lib
   $(MYNTEYED_SDK_ROOT)\3rdparty\opencv\build\x64\vc15\lib

..  image:: ../static/images/projects/vs2017/7_config_lib_dir.png

添加以下库到 “Additional Dependencies” ，

.. code:: bash

   mynteye_depth.lib
   opencv_world343.lib

.. image:: ../static/images/projects/vs2017/8_config_lib.png

使用SDK
-------

添加头文件和使用 API ，

.. image:: ../static/images/projects/vs2017/9_run_x64.png

选择 “Release x64” 来运行项目。










