SDK 安装
====================
1. 从文档 `SDK下载 <https://mynt-eye-d-sdk.readthedocs.io/zh_CN/latest/android_sdk/sdk_download.html>`__ 获取sdk资源。
2. 新建android工程，以Android Studio 为例。
3. 将下载的资源解压，解压出的aar文件放入libs目录(app / libs)
4. 在build.gradle添加aar的支持, 如下：

::

   dependencies {
       implementation fileTree(include: ['*.aar'], dir: 'libs')
       ....
   }
   
5. Build --> Make Project
