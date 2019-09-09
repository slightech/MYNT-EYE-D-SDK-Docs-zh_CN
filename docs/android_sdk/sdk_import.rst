SDK 安装
====================

1. 将SDK的aar文件放入libs目录
2. 在build.gradle添加aar的支持

::

   dependencies {
       implementation fileTree(include: ['*.aar'], dir: 'libs')
       ....
   }
