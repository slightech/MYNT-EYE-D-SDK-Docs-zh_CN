获取图像信息
======================

设置图像信息回调
~~~~~~~~~~~~~~~~

.. code:: kotlin

    mCamera?.setFrameCallback { data ->
        if (data.flag == FrameData.DEPTH) {
            // 深度图
        }
        if (data.flag == FrameData.COLOR) {
            // 彩色图
        }
    }