设备插拔监听
======================

初始化USBMonitor
~~~~~~~~~~~~~~~~

.. code:: kotlin

   mUSBMonitor = USBMonitor(mContext, object : USBMonitor.IUSBMonitorListener {

       override fun didFoundCamera(camera: MYNTCamera) {
           // 设备插入
       }

       override fun didDettach(camera: MYNTCamera) {
           // 设备拔出
       }

       override fun didConnectedCamera(camera: MYNTCamera) {
           // 连接成功
       }

       override fun didDisconnectedCamera(camera: MYNTCamera) {
           // 断开
       }

   })

注册USBMonitor（启动监听USB）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: kotlin

   mUSBMonitor?.register()

注销USBMonitor（停止监听USB）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: kotlin

   mUSBMonitor?.unregister()

释放USBMonitor
~~~~~~~~~~~~~~

.. code:: kotlin

   mUSBMonitor?.destroy()