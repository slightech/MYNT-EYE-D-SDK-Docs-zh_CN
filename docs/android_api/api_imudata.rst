ImuData （带IMU机型）
======================

数据类型
~~~~~~~~~~

.. code:: java

    /**
     * Data type
     *
     * 1: accelerometer
     * 2: gyroscope
     *
     * */
    public int flag;

时间戳
~~~~~~~~~~

.. code:: java

    public long timestamp;

温度
~~~~~~~~~~

.. code:: java

    public double temperature;

数据
~~~~~~~~~~

.. code:: java

    /**
     * Imu accelerometer data for 3-axis: X, Y, X.
     * Imu gyroscope data for 3-axis: X, Y, Z.
     *
     * */
    public double value[];