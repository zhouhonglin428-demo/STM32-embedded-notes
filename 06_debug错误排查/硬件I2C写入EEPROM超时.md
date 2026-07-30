![Snipaste_2026-07-30_15-45-20](./assets/Snipaste_2026-07-30_15-45-20.png)

![Snipaste_2026-07-30_15-45-32](./assets/Snipaste_2026-07-30_15-45-32.png)

串口输出：I2C error occur,code=1

现象错误分析：卡在 while(I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_MODE_SELECT) != SUCCESS) 循环

原因：观察SR2寄存器换算成二进制查找BUSY位显示BUSY == 1，它认为当前总线正在被占用。

重新观察开发板，发现我的逻辑分析仪之前测I2C的时候忘记拔了