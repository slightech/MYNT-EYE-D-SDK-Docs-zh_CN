MYNTCamera
======================

是否已连接
~~~~~~~~~~

.. code:: java

    public boolean isConnected()

是否开始预览
~~~~~~~~~~~~

.. code:: java

   public boolean isStart()

是否已打开相机
~~~~~~~~~~~~~~

.. code:: java

   public boolean isOpen()

是否是USB3.0
~~~~~~~~~~~~

.. code:: java

   public boolean getIsUSB3()

是否支持IMU
~~~~~~~~~~~

.. code:: java

   public boolean isIMUSupported()

设备序列号
~~~~~~~~~~

.. code:: java

   public String getSerialNumber()

设备名
~~~~~~

.. code:: java

   public String getName()

设备类型
~~~~~~~~

.. code:: java

   public int getCameraType()

设置相机的连接回调
~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setCameraListener(ICameraListener callback)

设置IMU信息的回调 （带IMU机型）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setImuCallback(IIMUCallback callback)

设置图像的回调
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setFrameCallback(IFrameCallback callback)

连接相机
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void connect()

打开相机
~~~~~~~~

.. code:: java

   public int open()

关闭相机
~~~~~~~~

.. code:: java

   public void close()

开始预览（IMU / VIDEO / ALL）[废弃]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public boolean start(Source source)



开始预览（IMU / VIDEO / ALL）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public boolean start(Source source, Frame frame)


释放相机
~~~~~~~~

.. code:: java

   public void destroy()


设置深度类型 （8bit / 11bit）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setDepthType(short depthType)

获取深度类型
~~~~~~~~~~~~

.. code:: java

   public short getDepthType()

设置预览分辨率 （480 / 720）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setPreviewSize(int height)

获取预览分辨率宽度
~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getPreviewWidth()

获取预览分辨率高度
~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getPreviewHeight()

设置预览用的Surface
~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setPreviewDisplay(Surface surface, Frame frame)

获取UVC FPS
~~~~~~~~~~~

.. code:: java

   public double getUVCFPS(Frame frame)

获取Preview FPS
~~~~~~~~~~~~~~~

.. code:: java

   public double getPreviewFPS(Frame frame)

获取相机内参
~~~~~~~~~~~~

.. code:: java

   public RectifyLogData getRectifyLogData()

检测是否支持IR
~~~~~~~~~~~~~~

.. code:: java

   public boolean isIRSupported()

设置IR值
~~~~~~~~

.. code:: java

   public int setIRCurrentValue(int value)

设置彩色图左右目预览
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setColorMode(ColorFrame colorFrame)
   
获取当前彩色数据
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public FrameData getColorFrameData()

获取当前深度数据
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public FrameData getDepthFrameData()

获取当前IR值
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getIRCurrentValue()

获取IR最小支持值
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getIRMinValue()

获取IR最大支持值
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getIRMaxValue()


将像素点对应的下标，转换为距离信息（单位 mm）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public int getDistanceValue(int index)


获取自动曝光开启状态
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public boolean getAEStatusEnabled()


开启自动曝光
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setEnableAE()


关闭自动曝光
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setDisableAE()


获取自动白平衡开启状态
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public boolean getAWBStatusEnabled()


开启自动白平衡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setEnableAWB()


关闭自动白平衡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setDisableAWB()


开关帧率显示
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void setEnableFrameFPS(boolean enable, int camera_switch)

保存指定距离内的点云
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public void savePointCloud(final FrameData colorFrameData,
                              final FrameData depthFrameData,
                              final String filePath,
                              Boolean hasColor,
                              int distance)