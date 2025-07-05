# OGX-Mini
![OGX-Mini Boards](images/OGX-Mini-github.jpg "OGX-Mini Boards")

本项目基于提供
适用于 RP2040 的固件，能够模拟多种游戏机的游戏手柄。该固件有多种版本，支持以下设备：
[Adafruit Feather USB 主机板](https://www.adafruit.com/product/5723)、树莓派 Pico、树莓派 Pico 2、树莓派 Pico W、树莓派 Pico 2 W、Waveshare RP2040-Zero、Pico/ESP32 混合板以及 4 通道 RP2040-Zero 配置。

[**访问网页配置程序**](https://conswapp.pages.dev/) ，以更改您的映射和死区设置。要通过 USB 将 OGX-Mini 与网页应用程序配对，请插入控制器，然后将其连接到您的电脑，按住
**
开始 + 左扳机 + 右扳机
**
进入网页应用程序模式。在网页应用程序中点击 “通过 USB 连接”，然后选择 OGX-Mini。您也可以通过蓝牙配对，这种情况下无需额外步骤。

## 支持的平台
- Original Xbox
- Playstation 3
- Nintendo Switch (docked)
- XInput (在XBOX360上使用，需要为360安装 [**UsbdSecPatch**](https://github.com/InvoxiPlayGames/UsbdSecPatch) 补丁。或者在刷写NAND时在J-Runner中选择补丁。)
- Playstation Classic
- DInput

## 切换平台
默认情况下，OGX-Mini 将模拟初代 Xbox 控制器，您必须按住组合按键 3 秒钟，以切换您想要游玩的平台。您选择的模式在设备断电后仍会保留。


Start = Plus (Switch) = Options (Dualsense/DS4)

- XInput
    - Start + Dpad Up 
- Original Xbox
    - Start + Dpad Right
- Original Xbox Steel Battalion
    - Start + Dpad Right + Right Bumper
- Original Xbox DVD Remote
    - Start + Dpad Right + Left Bumper
- Switch
    - Start + Dpad Down
- PlayStation 3
    - Start + Dpad Left
- PlayStation Classic
    - Start + A (Cross for PlayStation and B for Switch gamepads)
- Web Application Mode
    - Start + Left Bumper + Right Bumper

存储新的模式后，RP2040 将自行复位，因此无需将其拔下。

## Supported devices
### Wired controllers
- Original Xbox Duke and S
- Xbox 360, One, Series, and Elite
- Dualshock 3 (PS3)
- Dualshock 4 (PS4)
- Dualsense (PS5)
- Nintendo Switch Pro
- Nintendo Switch wired
- Nintendo 64 Generic USB
- Playstation Classic
- Generic DInput
- Generic HID (mappings may need to be editted in the web app)

注意：有一些第三方控制器可以更改其供应商识别码（VID）/ 产品识别码（PID），这些控制器可能无法正常工作。

### 无线适配器
- Xbox 360 电脑适配器（微软原装或仿制产品）
- 8Bitdo v1 和 v2 蓝牙适配器（设置为 XInput 模式）
- 大多数能模拟成 Switch/XInput/PlayStation 控制器的无线适配器应该都能使用

### 无线蓝牙控制器（Pico W 和 ESP32）
**注意:** 蓝牙功能尚处于早期测试阶段，部分功能可能存在异常。
- Xbox Series、Xbox One 和 Xbox Elite 2
- Dualshock 3
- Dualshock 4
- Dualsense
- Switch Pro
- Steam
- Stadia
- 以及更多

Please visit [**this page**](https://bluepad32.readthedocs.io/en/latest/supported_gamepads/) for a more comprehensive list of supported controllers and Bluetooth pairing instructions.

## v1.0.0 新增功能
- 为 Pico W、Pico 2 W 和 Pico+ESP32 提供蓝牙功能。
- 网页应用程序（可通过 USB 或蓝牙连接），用于配置死区和按键映射，支持最多 8 个保存的配置文件。
- 支持 Pi Pico 2 和 Pico 2 W（RP2350）。
- 延迟降低约 3 - 4 毫秒，对比图表即将推出。
- 4 通道功能，连接 4 个 Pico，并使用一个 Xbox 360 无线适配器控制全部 4 个设备。
- 延迟 USB 挂载，直到插入控制器，这对内部安装很有用（仅适用于非蓝牙板）。
- 支持通用 HID 控制器。
- 模拟 Dualshock 3（不含陀螺仪），震动功能现已可用。
- 使用无线 Xbox 360 聊天板模拟 Steel Battalion 控制器。
- 模拟 Xbox DVD 加密狗。你必须提供或转储自己的加密狗固件，详见 “Tools” 目录。
- 支持初代 Xbox 和 PS3 的模拟按键。
- 为 RP2040 - Zero 和 Adafruit Feather 开发板提供 RGB LED 支持。

## Planned additions
- More accurate report parser for unknown HID controllers
- Hardware design for internal OG Xbox install
- Hardware design for 4 channel RP2040-Zero adapter
- Wired Xbox 360 chatpad support
- Wired Xbox One chatpad support
- Switch (as input) rumble support
- OG Xbox communicator support (in some form)
- Generic bluetooth dongle support
- Button macros
- Rumble settings (intensity, enabled/disable, etc.)

## Hardware
For Pi Pico, RP2040-Zero, 4 channel, and ESP32 configurations, please see the hardware folder for diagrams.

I've designed a PCB for the RP2040-Zero so you can make a small form-factor adapter yourself. The gerber files, schematic, and BOM are in Hardware folder.

<img src="images/OGX-Mini-rpzero-int.jpg" alt="OGX-Mini Boards" width="400">

If you would like a prebuilt unit, you can purchase one, with cable and Xbox adapter included, from my [**Etsy store**](https://www.etsy.com/listing/1426992904/ogx-mini-controller-adapter-for-original).

## Adding supported controllers
If your third party controller isn't working, but the original version is listed above, send me the device's VID and PID and I'll add it so it's recognized properly.

## Build
### RP2040
You can compile this for different boards with the CMake argument ```OGXM_BOARD``` while configuring the project. 

The options are:
- ```PI_PICO``` 
- ```PI_PICO2``` 
- ```PI_PICOW``` 
- ```PI_PICO2W``` 
- ```RP_ZERO``` 
- ```ADA_FEATHER``` 
- ```PICO_ESP32``` 
- ```EXTERNAL_4CH```

You can also set ```MAX_GAMEPADS``` which, if greater than one, will only support DInput (PS3) and Switch.

You'll need git, python3, CMake, Ninja and the GCC ARM toolchain installed. CMake scripts will patch some files in Bluepad32 and BTStack and also make sure all git submodules (plus their submodules and dependencies) are downloaded. Here's an example on Windows:
```
git clone --recursive https://github.com/wiredopposite/OGX-Mini.git
cd OGX-Mini/Firmware/RP2040
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DOGXM_BOARD=PI_PICOW -DMAX_GAMEPADS=1
cmake --build build
```
Or just install the GCC ARM toolchain and use the CMake Tools extension in VSCode.

### ESP32
Please see the Hardware directory for a diagram showing how to hookup the ESP32 to your RP2040.

You will need ESP-IDF v5.1, esptool, python3, and git installed. If you use VSCode, you can install the ESP-IDF extension and configure the project for ESP-IDF v5.1, it'll download everything for you and then you just click the build button at the bottom of the window.

When you build with ESP-IDF, Cmake will run a python script that copies the necessary BTStack files into the components directory, this is needed since BTStack isn't configured as an ESP-IDF component when you download it with git. 
