~~~ c
 DMA_InitStructure.DMA_MemoryInc = DMA_MemoryInc_Enable;
DMA_InitStructure.DMA_PeripheralInc = DMA_PeripheralInc_Enable;

~~~

这个Peripheral虽然指的是外设，但是在存储器到存储器模式下，DMA 把“外设接口”当成了“第二个内存”来	用。