FrameData
======================

数据类型
~~~~~~~~~~

.. code:: java

    /**
     *
     * FrameData.COLOR
     * FrameData.DEPTH
     *
     * */
    public int flag;

时间戳
~~~~~~~~~~

.. code:: java

    public int frameId;


图像宽度
~~~~~~~~~~

.. code:: java

    public int width;

图像高度
~~~~~~~~~~

.. code:: java

    public int height;

彩色图像类型（左目 / 左目 && 右目）
~~~~~~~~~~

.. code:: java

    public ColorFrame colorMode;

图像类型
~~~~~~~~~~

.. code:: java
    
    /**
     * MYNTCamera.FRAME_FORMAT_YUYV
     * MYNTCamera.FRAME_FORMAT_MJPEG
     * MYNTCamera.PIXEL_FORMAT_RGBX
     *
     * */
    public int type;

深度图类型
~~~~~~~~~~

.. code:: java

    /**
     * MYNTCamera.DEPTH_DATA_11_BITS
     * MYNTCamera.DEPTH_DATA_8_BITS
     *
     * */
    public int depthType;

获取bitmap
~~~~~~~~~~

.. code:: java

    public Bitmap convert2Bitmap(byte[] bytes, int width, int height)

获取左目数据
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public byte[] getLeftBytes()

获取右目数据
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public byte[] getRightBytes()


获取距离数组（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public int[] getDistanceInts()

获取距离数组（只有flag为DEPTH时, 可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    /**
     * 获取距离表（int）
     *
     * @param max   最大值（mm），如果超过max，自动变为0
     *
     * */
    public int[] getDistanceInts(int max)
    
获取距离数组（只有flag为DEPTH时, 可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    /**
     * 获取距离表（int）
     *
     * @param min   最小值（mm）
     * @param max   最大值（mm），如果超过max，自动变为min
     *
     * */
    public int[] getDistanceInts(int min, int max)


获取距离数组（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public byte[] getDistanceShorts()

获取距离表（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    /**
     * 获取距离表（int）
     *
     * @param max   最大值（mm），如果超过max，自动变为0
     *
     * */
    public byte[] getDistanceShorts(int max)

获取距离表（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    /**
     * 获取距离表（short）
     *
     * @param min   最小值（mm）
     * @param max   最大值（mm），如果超过max，自动变为min
     *
     * */
    public byte[] getDistanceShorts(int min, int max)


获取距离（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public int getDistanceValue(int index)

获取距离（只有flag为DEPTH时，可用）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

    public int getDistanceValue(int x, int y)