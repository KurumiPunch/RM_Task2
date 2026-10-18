## 项目简介
---- 
#### 功能:
	PWM呼吸灯,按键控制LED,UART串口通信
#### Toolchain:
	MDK-ARM
#### 接线:
- PA6-->1k电阻-->LED+-->GND
- PB1-->  按键  -->GND
- PB0-->1k电阻-->LED+-->GND
- PA9-->TTL转USB的RXD
- PA10-->TTL转USB的TXD
- TTL转USB的GND-->GND
---- 
### 工程说明
----
#### CubeMX配置:
	HCLK:72MHz
	PWM呼吸灯:
		- PA6 TIM3_CH1 Channel1 PWM Generation CH1
		- 预分频器:72-1
		- 自动重装载值:1000-1
		- NVIC global interrupt : add
	
	按键控制LED:
		- PB0 Label:Button_LED Function:GPIO_Output GPIO_Mode:推挽输出
		- PB1 Label:Button_Detect Function:GPIO_EXTI1 PullUp 
		  Mode:外部下降沿触发中断
		  EXTI line1 Interrupt:add Preemption Priority:15
	UART串口通信:
		- PA10 Function:USART1_RX 模式:异步 DMA1Channel5
		- PA9 Function: USART1_TX 模式:异步 DMA1Channel4
---- 
#### 实现代码:
	所有手写非CubeMX生成的都放在main.h和main.c
1. HAL_TIM_PeriodElapsedCallback 实现呼吸灯
   - 通过设置比较寄存器的值改变PWM输出电平
2. HAL_UARTEx_RxEventCallback 将收到的数据发回
3. HAL_GPIO_EXTI_Callback 检测按键触发的电平下降沿,触发中断从而实现点灯