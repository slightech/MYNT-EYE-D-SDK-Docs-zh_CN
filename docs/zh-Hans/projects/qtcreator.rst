.. role:: raw-latex(raw)
   :format: latex
..

.. _qtcreator:

Qt Creator 如何使用 SDK
=======================

该教程将会使用 Qt creator 创建 Qt 项目来运行 SDK 。

   你可以在 ``<sdk>/platforms/projects/qtcreator`` 目录下找到工程样例。

准备
----

-  Windows: 安装 SDK 的 exe 包
-  Linux: 使用源代码编译和 ``make install``

创建项目
--------

打开 Qt Creator ，然后 ``New Project``\ ，

|image0|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project.png}`
:raw-latex:`\endlatexonly`

选择 ``Qt Widgets Application`` ，

|image1|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project2.png}`
:raw-latex:`\endlatexonly`

设置项目位置和名字，

|image2|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project3.png}`
:raw-latex:`\endlatexonly`

选择 build kits ，

|image3|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project4.png}`
:raw-latex:`\endlatexonly`

然后他将会生成框架源文件，

|image4|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project5.png}`
:raw-latex:`\endlatexonly`

|image5|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project6.png}`
:raw-latex:`\endlatexonly`

最后，你将会看到这样的新项目工程，

|image6|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{new_project7.png}`
:raw-latex:`\endlatexonly`

配置项目
--------

添加 ``INCLUDEPATH`` 和 ``LIBS`` 到 ``mynteyed_demo.pro`` 。

.. code:: bash

   win32 {
       SDK_ROOT = "$$(MYNTEYED_SDK_ROOT)"
       isEmpty(SDK_ROOT) {
           error( "MYNTEYED_SDK_ROOT not found, please install SDK firstly" )
       }
       message("SDK_ROOT: $$SDK_ROOT")

       INCLUDEPATH += "$$SDK_ROOT/include"
       LIBS += "$$SDK_ROOT/lib/mynteye_depth.lib"
   }

   unix {
       INCLUDEPATH += /usr/local/include
       LIBS += -L/usr/local/lib -lmynteye_depth
   }

使用SDK
-------

可以参考工程样例添加头文件和使用 API 。

Windows
~~~~~~~

选择 “Release” 来运行项目。

|image7|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=0.5\textwidth]{release_run.png}`
:raw-latex:`\endlatexonly`

然后你将看到主窗口，

|image8|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{run_win.png}`
:raw-latex:`\endlatexonly`

Linux
~~~~~

运行项目，你将看到主窗口，

|image9|

.. raw:: latex

   \latexonly

:raw-latex:`\includegraphics[width=1\textwidth]{run_linux.png}`
:raw-latex:`\endlatexonly`

.. |image0| image:: ../../static/images/projects/qtcreator/new_project.png
.. |image1| image:: ../../static/images/projects/qtcreator/new_project2.png
.. |image2| image:: ../../static/images/projects/qtcreator/new_project3.png
.. |image3| image:: ../../static/images/projects/qtcreator/new_project4.png
.. |image4| image:: ../../static/images/projects/qtcreator/new_project5.png
.. |image5| image:: ../../static/images/projects/qtcreator/new_project6.png
.. |image6| image:: ../../static/images/projects/qtcreator/new_project7.png
.. |image7| image:: ../../static/images/projects/qtcreator/release_run.png
.. |image8| image:: ../../static/images/projects/qtcreator/run_win.png
.. |image9| image:: ../../static/images/projects/qtcreator/run_linux.png
