### 01. DMA发送串口数据乱码或程序卡死

- **故障现象**：使用 DMA M to P 模式向串口 TX 发送数据时，上位机收到乱码，或者传输一次后程序卡死。
- **底层原因**：使能了串口本身的发送中断，导致 CPU 与 DMA 抢夺 `USART_DR` 寄存器的控制权。
- **标准解法**：
  
  **错误操作**：保留了串口中断配置 `USART_ITConfig(USART1, USART_IT_TXE, ENABLE);`
  
  **正确操作**：
  
  1. 彻底禁用串口发送中断，改用 `USART_DMACmd(USART1, USART_DMAReq_Tx, ENABLE);`
  2. 若需判断发送完成，去查询 DMA 的标志位 `DMA_GetFlagStatus()` 或开启 DMA 自己的中断（TCIE），决不能开串口发送中断。