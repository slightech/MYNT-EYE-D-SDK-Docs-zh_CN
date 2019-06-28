.. _calibration_tool:

MYNT EYE D 标定说明
==========



介绍
--------

该手动标定工具可以生成校准数据和ZD表格（计算距离差异)。手动标定主要与两个参数有关：1.棋盘的大小  2.棋盘与双目相机之间的距离

* 棋盘与相机模块之间的距离，建议是目标应用的工作距离。

* 棋盘的推荐尺寸，建议是棋盘的大小应该覆盖预览图像最大尺寸的50%。

校准过程 1 (Yoffset)
--------

* 校准过程 1 需要1张图片。
* 棋盘必须在相机的前方，并且覆盖预览图像尽可能大的面积（超过50%）。
* 按下 “c”或者 “C” 获得正确位置的棋盘照片。


操作指南
--------

1.双击打开 eSPCalibrator.exe文件
2.按下 “c”或者 “C”来拍摄快照（总共1帧）

.. image:: ../images/calibration001.png
   :width: 60%



校准过程 2 (Calibration)
--------

* 校准过程 2 需要5个不同角度的5张图片。

* 所需的角度是将 X 轴沿 Y 轴旋转，每次旋转 10°或者30°。也可以讲 Y 轴沿 X 轴旋转。

* 棋盘覆盖的最大面积，必须超过相机预览图像的 50%。

* 按下 “c”或者 “C” 获得正确位置的棋盘照片。如果校准器无法检测到棋盘上的所有交叉点，将会获得“未找到”的结果。

操作指南
--------

.. image:: ../images/calibration002.png
   :width: 60%

校准结果
-------

.. image:: ../images/calibration003.png
   :width: 60%

eSPCalibrator 的参数
-------

.. image:: ../images/calibration004.png
   :width: 60%

1. 打开 eDepthK.prj 文件
2. 注意'Col1''Row1''Size1'必须与棋盘相匹配

11x7交叉棋盘示例
-------

.. image:: ../images/calibration005.png
   :width: 60%


日志文件
-------

.. image:: ../images/calibration006.png
   :width: 60%

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

FW 版本校验
-------

下面版本的 FW已验证过. 其它未验证的版本不保证能正常使用。

1. EX8031-B01-B0135P-BL60U-011-EnDepthPostProcess(U3 HD,VGA)
2. EX8036-B01-B0135P-BL60U-011-EnDepthPostProcess(U3 HD,VGA)
3. EX8037-B01-A9714M-BL40U-005-EnDepthPostProcess(U2 HD,VGA)
4. EX8038-B01-B0144M-BL60U-002(U3 HD)
5. Vivian-B01-B0135P-BL60U-006(U3 color 1920x960, calibrationcolor 1440x720 depth 580x580)

因为 Yoffset的传感器互换，所以无法正常工作






