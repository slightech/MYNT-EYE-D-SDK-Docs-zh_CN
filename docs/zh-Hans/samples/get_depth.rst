.. _get_depth:

获取深度图像
============

深度图像，属于上层合成数据。

可以通过设置\ ``depth_mode``\ 来改变深度图显示。

.. code-block:: c++

   // Depth mode: colorful(default), gray, raw
   params.depth_mode = DepthMode::DEPTH_RAW;

然后使用\ ``GetStreamData()``\ 获取。另外，判断不为空后再使用。

参考代码片段：

.. code-block:: c++

   auto image_depth = cam.GetStreamData(ImageType::IMAGE_DEPTH);
   if (image_depth.img) {
     cv::Mat depth = image_depth.img->To(ImageFormat::DEPTH_RAW)->ToMat();

     cv::setMouseCallback("depth", OnDepthMouseCallback, &depth_region);
     // Note: DrawRect will change some depth values to show the rect.
     depth_region.DrawRect(depth);
     cv::imshow("depth", depth);

     depth_region.ShowElems<ushort>(depth, [](const ushort& elem) {
       return std::to_string(elem);
     }, 80, depth_info);
   }

上述代码，用了 OpenCV 来显示图像。选中显示窗口时，按 ESC/Q
就会结束程序。

.. note::

  get_depth样例仅支持使用DEPTH_RAW模式，可以修改其他样例的depth_mode来获得其他模式的深度图。

完整代码样例，请见\ `get_depth.cc <https://github.com/slightech/MYNT-EYE-D-SDK/blob/master/samples/src/get_depth.cc>`__
。
