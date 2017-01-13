<!--toc-->

- [名词约定](#名词约定)
- [平台支持](#平台支持)
- [目录介绍](#目录介绍)
- [按键说明](#按键说明)
- [开发指南](#开发指南)
	- [Android手机运行环境安装](#android手机运行环境安装)
		- [1 应用安装](#1-应用安装)
		- [2 手柄配对](#2-手柄配对)
		- [3 应用权限检查](#3-应用权限检查)
		- [4 测试emo](#4-测试emo)
		- [5 演示demo](#5-演示demo)
	- [Unity SDK](#unity-sdk)
	- [Android SDK](#android-sdk)
		- [API说明](#api说明)
			- [1) com.ximmerse.sdk.XDeviceApi](#1-comximmersesdkxdeviceapi)
			- [2) com.ximmerse.sdk.XDeviceConstants](#2-comximmersesdkxdeviceconstants)
			- [3) com.ximmerse.input.ControllerInput.State](#3-comximmerseinputcontrollerinputstate)

<!-- tocstop -->




# 名词约定

名称 | 解释
---|---
controller | 手柄
HMD | 头戴显示器，即VR头显
X-Cobra|手柄的别称



# 平台支持
* 开发调试平台支持:
	* Windows 7/8/10
* 目标平台支持:
	* Android
* 3D引擎支持:
	* Unity3D

# 目录介绍
* **Demo**  	  ：针对主流的HMD，提供演示DEMO
* **Drivers**   ：平台驱动程序
* **Document\3DOF** ：说明文档
* **Native Android**：Android版本的SDK   
* **Native C++**：Windows C\++版本的SDK  
* **Tools**：工具包  
* **Unity**：Unity插件
* **Unreal**：Unreal插件  

&emsp;
# 按键说明
<div align = center>
<img src="./imgs/key_map.png" width="200">
</div>

>  注：短按'home'键回中

&emsp;
# 开发指南

&emsp;
## Android手机运行环境安装

### 1 应用安装
1.1 在android手机上安装如下两个apk
> - [BTConfig.apk](https://github.com/Ximmerse/SDK/blob/master/Tools/AndroidXimService/BTConfig1.0.10(service-v2.0.1).apk): 用于手柄配对的工具
> - [DeviceTest.apk](https://github.com/Ximmerse/SDK/blob/master/Tools/AndroidXimService/DeviceTest.apk)：用于测试设备的工具，可以在手机上输出rotation、button等信息

&emsp;
### 2 手柄配对

2.1 装入电池，手柄自动开机。

2.2 打开手机上的蓝牙功能，并打开BTConfig工具。
>- 如果第一次打开BTConfig，会推荐安装"Ximmerse Service"，选择"Next"而后点击"Install"；

<div align = center>
<img src="../../Tools/imgs/initial_btconfig_launch.png" width="400">
</div>
<div align = center>
<img src="../../Tools/imgs/install_xim_service.png" width="400">
</div>

2.3 先按下BTConfig的Controller(R)的“Scan”按钮，然后同时按着手柄的'APP'和'HOME'键，配对成功后手柄状态变为"Paired"，退出应用；

> 手柄只需要配对一次；更换新的手柄时，重复“手柄配对”的步骤即可

<div align = center>
<img src="../../Tools/imgs/btconfig.png" width="400">
</div>
<div align = center>
<img src="./imgs/controller_paired.png" width="400">
</div>

&emsp;
### 3 应用权限检查
打开Application Manager，找到"Ximmerse Service Launcher"，点击"permissions",确认"location"和"storage"权限是打开的；这个步骤只需要做一次。
<div align = center>
<img src="../../Tools/imgs/application_manager_app_info.png" width="400">
</div>

&emsp;
### 4 测试demo
设备和手机保持连接状态，运行[Device Test](https://github.com/Ximmerse/SDK/raw/master/Tools/AndroidXimService/DeviceTest.apk)，通过界面可观察到从手柄姿态、按键等信息。

<div align = center>
<img src="../../Tools/imgs/test_app.png" width="400">
</div>  

&emsp;
### 5 演示demo
名称 | HMD
---|---
[Playground(Cardboards)](https://github.com/Ximmerse/SDK/blob/master/Demos/3DOF/Playground(Cardboards).apk) | Google Cardboards
[Playground(Gear VR)](https://github.com/Ximmerse/SDK/blob/master/Demos/3DOF/Playground(Gear%20VR).apk) | 三星Gear VR

&emsp;
## Unity SDK
获取unity插件和使用说明，请点击[地址](https://github.com/Ximmerse/SDK/tree/master/Unity).  

获取unity插件的FAQ，请点击[地址](https://github.com/Ximmerse/SDK/blob/master/Unity/FQA.md).  

获取unity插件API说明，请点击[地址](https://github.com/Ximmerse/SDK/blob/master/Unity/APIDoc.md).  


&emsp;
## Android SDK
获取Android SDK，请点击[地址](https://github.com/Ximmerse/SDK/tree/master/Native%20Android/DeviceTest)

&emsp;
### API说明
类名 | 用途
---|---
com.ximmerse.sdk.XDeviceApi| XDevice API接口，为静态方法
com.ximmerse.sdk.XDeviceConstants|XDevice 常量定义
com.ximmerse.input.ControllerInput | 手柄控制器
com.ximmerse.input.ControllerInput.State|手柄控制器消息
com.ximmerse.input.PositionalTracking | 位置跟踪器(3DOF Controller无该功能)  

&emsp;
#### 1) com.ximmerse.sdk.XDeviceApi

方法 | 用途
---|---
public static int init(Context context) | 初始化
public static int exit()|退出
public static int getInputDeviceHandle(String name) | 获取设备句柄
public static int updateInputState(int which) | 更新设备状态
public static int getInt(int which, int fieldID, int defaultValue) | 获取设备int域的属性,属性定义参见XDeviceConstants
public static boolean getBool(int which, int fieldID, boolean defaultValue)|获取设备boolean域的属性
public static float getFloat(int which, int fieldID, float defaultValue) |获取设备Float域的属性
public static int sendMessage(int which, int Msg, int wParam, int lParam) |向设备发送消息
&emsp;
#### 2) com.ximmerse.sdk.XDeviceConstants
设备属性 | 用途
---|---
kField_ConnectionState | 设备连接状态
kField_BatteryLevel|设备电量
kField_ErrorCode|错误码

设备连接状态|说明
---|---
kConnectionState_Disconnected|断开连接
kConnectionState_Scanning|正在扫描
kConnectionState_Connecting|正在连接
kConnectionState_Connected|已经连接
kConnectionState_Error|连接错误，可通过读取设备的ErrorCode获取错误码

消息(Message)|说明
---|---
kMessage_TriggerVibration|电机振动
kMessage_RecenterSensor|回中

&emsp;
#### 3) com.ximmerse.input.ControllerInput.State
> 按键定义请参考[microsoft gamepad](https://msdn.microsoft.com/en-us/library/windows/apps/microsoft.directx_sdk.reference.xinput_gamepad)

方法|说明
---|---
public void updateState() |更新状态
public boolean getButton(int buttonMask)|获取按键事件
public boolean getButtonDown(int buttonMask)|按键按下
public boolean getButtonUp(int buttonMask)|按键弹起
public float getAxis(int axisIndex)|获取Axis，参考Axis定义
public boolean getRotation(float[] dest,int offset)|获取手柄姿态
> 注：接口为主动式获取接口

 buttonMask|说明
 ---|---
 BUTTON_DPAD_UP|触摸板上按键
 BUTTON_DPAD_DOWN|触摸板下按键
 BUTTON_DPAD_LEFT|触摸板左按键
 BUTTON_DPAD_RIGHT|触摸板右按键
 BUTTON_START|APP键
 BUTTON_BACK|Home键

触摸事件|说明
---|---
BUTTON_LEFT_THUMB_UP|上点击事件
BUTTON_LEFT_THUMB_DOWN|下点击事件
BUTTON_LEFT_THUMB_LEFT|左点击事件
BUTTON_LEFT_THUMB_RIGHT|右点击事件
BUTTON_LEFT_THUMB_MOVE|触摸事件


Axis定义|说明
---|---
AXIS_LEFT_TRIGGER|trigger键值
AXIS_LEFT_THUMB_X|触摸板x轴
AXIS_LEFT_THUMB_Y|触摸板y轴
