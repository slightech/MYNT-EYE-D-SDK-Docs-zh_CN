.. _depth_filter:

使用filter进行深度数据的滤波
==============================

滤波器类型统一继承自 ``BaseFilter`` 。

方法口协议如下：

.. code-block:: c++

    virtual bool ProcessFrame(
          std::shared_ptr<Image> out,
          const std::shared_ptr<Image> in) = 0; // NOLINT
      virtual bool LoadConfig(void* data);

    inline bool TurnOn();
    inline bool TurnOff();
    inline bool IsEnable();


    int main(int argc, char const* argv[]) {
    ...

    SpatialFilter spat_filter;
    TemporalFilter temp_filter;

    ...
    for (;;) {
      // get frame
      ...
      spat_filter.ProcessFrame(image_depth.img, image_depth.img);
      temp_filter.ProcessFrame(image_depth.img, image_depth.img);
      ...
    }


.. tip::

    使用时，实例化一个 ``Filter`` ，然后直接在图像处理循环中使用 ``ProcessFrame`` ，方法如上。
    图像会实时随图像信息变化自适应，也可以实时的使用 ``TurnOn/TurnOff`` 开关。