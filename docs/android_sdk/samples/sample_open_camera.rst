打开相机
======================

设置Camera连接回调
~~~~~~~~~~~~~~~~~~

.. code:: kotlin

   mCamera?.setCameraListener(object : MYNTCamera.ICameraListener {

       override fun didConnectedCamera(camera: MYNTCamera?) {

       }

       override fun didDisconnectedCamera(camera: MYNTCamera?) {

       }
   })

连接相机 （会弹出权限对话框）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: kotlin

   mCamera?.connect()

连接成功后，开始获取数据
~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: kotlin

   //打开设备
   mCamera?.open()
   // 设置IR
   mCamera?.irCurrentValue = IR_DEFAULT_VALUE

   backgroundHandler?.post {
       if (mCamera == null) return@post
       // 彩色图预览相关的对象
       mColorSurface = Surface(colorTextureView.surfaceTexture)
       // 深度图预览相关的对象
       mDepthSurface = Surface(depthTextureView.surfaceTexture)

       mCamera?.setPreviewDisplay(mDepthSurface, MYNTCamera.Frame.DEPTH)
       mCamera?.setPreviewDisplay(mColorSurface, MYNTCamera.Frame.COLOR)
       // 设置预览尺寸 (480 / 720)
       mCamera?.setPreviewSize(previewSize.height)
       // 设置深度类型 8bit / 11bit
       mCamera?.setDepthType(depthType)
       // 设置图像回调
       mCamera?.setFrameCallback { data ->
           if (data.flag == FrameData.DEPTH) {
               // 深度图
           }
           if (data.flag == FrameData.COLOR) {
               // 彩色图
           }
       }
       // 开始预览
       mCamera?.start(MYNTCamera.Source.ALL, MYNTCamera.Frame.ALL)
   }