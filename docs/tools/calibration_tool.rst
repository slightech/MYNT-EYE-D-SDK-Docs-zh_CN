.. _calibration_tool:

MYNT EYE D 标定说明
==========


获取标定工具
------------

Latest tool:  mynteye-d-calibrator_1.0.zip `Google
Drive <https://drive.google.com/open?id=13QsqgkzNfh4yKDisYgHXtshzFyqRzbDs>`__,
`Baidu Pan <https://pan.baidu.com/s/11gbg_KkzaezNa52YfdMjJw>`__


准备工作(更新配置文件)
---------------------

* 深度版50°相机的配置文件存在于D1000-50文件夹, 深度版120°相机的配置文件存在于D1000-120文件夹。
* HD表示720P, VGA表示480P， 因为深度相机有2种分辨率，所以需要2次标定。
* 开始标定前把 HD或VGA 文件夹中的 ``eDepthK.prj`` 复制并替换到 ``mynteye-d-calibrator_1.0`` 文件夹下。
* 用记事本打开 ``eDepthK.prj`` 文件并找到 ``[Chess_Para]`` 部分，其中：将Col1/2/3/4 修改为标定板棋盘格的横向黑白交叉点数， Row1/2/3/4 修改为标定板棋盘格的纵向黑白交叉点数, Size1/2/3/4 修改为棋盘格格子边长，单位mm。

11x7交叉棋盘示例
-------

.. image:: ../images/calibration005.png
   :width: 80%

eSPCalibrator 的参数
-------

.. image:: ../images/calibration004.png
   :width: 80%

1. 打开 eDepthK.prj 文件
2. 注意'Col1''Row1''Size1'必须与棋盘相匹配


校准过程 1 (Yoffset)
--------------------

* 如果标定的是VGA模式，可以直接进行校准过程2。
* 校准过程 1 需要1张图片。
* 棋盘必须在相机的前方，并且覆盖预览图像尽可能大的面积（超过50%）。
* 按下 “c”或者 “C” 获得正确位置的棋盘照片。


操作指南
--------

1.双击打开 mynteye-d-calibrator.exe文件
2.按下 “c”或者 “C”来拍摄快照（总共1帧）

.. image:: ../images/calibration001.png
   :width: 60%



校准过程 2 (Calibration)
--------

* 校准过程 2 需要5个不同角度的5张图片。

* 所需的5张图片分别是 正对，左倾，右倾，上倾，下倾(角度在10°到30°内)。

* 棋盘覆盖的最大面积，必须超过相机预览图像的 50%。

* 按下 “c”或者 “C” 获得正确位置的棋盘照片。如果校准器无法检测到棋盘上的所有交叉点，将会获得“未找到”的结果。

操作指南
--------

.. image:: ../images/calibration002.png
   :width: 80%

校准结果
-------

* 标定完后标定参数会自动写入相机。

.. image:: ../images/calibration003.png
   :width: 80%

* 标定结束后日志文件 ``StereoSetting.txt`` 会保存左右目的 ``Reprojection error(重投影误差)`` ，标定结果，要求重投影误差最好能达到0.2或更低。如果超过0.5，需要重新标定。

日志文件
-------

* 标定后日志文件会保存到 ``Log_Folder`` 。

.. image:: ../images/calibration006.png
   :width: 80%

附录
-------

错误信息 : Yoffset
-------

========================================  ==================================================================
Error Message                             Possible root cause
========================================  ==================================================================
Yoffset Not support format.               1. FW issue, check page.14 2. eDepthK.prj setting error
No Device                                 1. USB unstable
Yoffset Cannot Preview Resolution         1. FW issue, check page.14 2. eDepthK.prj setting error                              
========================================  ==================================================================

错误信息 : Calibration
-------

========================================  ==================================================================
Error Message                             Possible root cause
========================================  ==================================================================
Calibration Not support format.           1. FW issue, check page.14  2. eDepthK.prj setting error
No Device                                 1. USB unstable
Calibration Cannot Preview Resolution     1. FW issue, check page.14 2. eDepthK.prj setting error
Calibration fail : Calib_Line_Buffer_Err  1. linebuffer > 160, quality error
Calibration fail : Calib_reproject_err    1. reprojection err > 1.75, quality error
Calibration Write flash fail              1. FW issue, check page.14
========================================  ==================================================================

错误信息 : ZD
-------

========================================  ==================================================================
Error Message                             Possible root cause
========================================  ==================================================================
ZD initialization Fail                    1. FW issue, check page.14 2. eDepthK.prj setting error
No Device                                 1. USB unstable
Cannot Preview Resolution                 1. FW issue, check page.14 2. eDepthK.prj setting error
Write ZD Table Fail                       1. FW issue, check page.14
========================================  ==================================================================







