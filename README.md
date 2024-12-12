# Kalama
<img src="https://github.com/user-attachments/assets/d5087af2-af5a-46d9-9443-214a3e933253" width="20%" />

## Kalama 热成像 简介

### 原理
STM32通过I2C与AMG8833通信获取图像数据，然后通过CDC串口发送图像数据到手机App，App再对原始图像进行双线性插值、插帧、上色，最终得到图像通过canvas显示到指定区域。

### 可优化选项
单片机使用STM32F103C8T6，实测关掉FreeRTOS和UART可以移植到STM32F103C6T6，进一步降低成本。

### 效果
热成像传感器采用的是我祖传的 AMG8833，8 * 8的像素实在是难以言表，即便是使用双线性插值也是一片模糊，啥也看不清。于是我添加了相机辅助模式（就是相机预览），效果还是很不错的。
再使用插帧后可以说相当丝滑了。

## 效果图：

<img src="https://github.com/user-attachments/assets/4fc86f87-64ba-4b01-9276-99af762d0eef" width="30%" />
<img src="https://github.com/user-attachments/assets/50e59feb-94f1-489f-aa2e-7ce9716a375b" width="30%" />
<img src="https://github.com/user-attachments/assets/0f7f2f33-ec6b-4654-9d08-418a2df31e1b" width="30%" />

<img src="https://github.com/user-attachments/assets/b129bdd9-5205-4cde-ad81-fbbbb7847d2b" width="30%" />

本来打算使用3D打印外壳，试着打印了一下，太臃肿了，于是直接把AMG焊上了。

<img src="https://github.com/user-attachments/assets/ceebc4d5-9b9c-4b6f-9a9b-6f26bc803b6d" width="30%" />


## 摄像机辅助原理

<img src="https://github.com/user-attachments/assets/48a271d9-b2d0-4410-b8e7-0332a9966792" width="50%" />

## 电路

PCB画的太拉跨了就不放出来了。

简单来说就是STM32最小系统板使用I2C_1连接AMG8833，USB接口连接手机就行了。

PC13连接LED（可选）。
