# OGX-Mini
![OGX-Mini Boards](images/OGX-Mini-github.jpg "OGX-Mini Boards")

Firmware for the RP2040, capable of emulating gamepads for several game consoles. The firmware comes in many flavors, supported on the [Adafruit Feather USB Host board](https://www.adafruit.com/product/5723), Pi Pico, Pi Pico 2, Pi Pico W, Pi Pico 2 W, Waveshare RP2040-Zero, Pico/ESP32 hybrid, and a 4-Channel RP2040-Zero setup.

[**Visit the web app here**](https://wiredopposite.github.io/OGX-Mini-WebApp/) to change your mappings and deadzone settings. To pair the OGX-Mini with the web app via USB, plug your controller in, then connect it to your PC, hold **Start + Left Bumper + Right Bumper** to enter web app mode. Click "Connect via USB" in the web app and select the OGX-Mini. You can also pair via Bluetooth, no extra steps are needed in that case. 

## 支持的平台
- 初代 Xbox
- Playstation 3
- Nintendo Switch (底座模式)
- XInput (use [**UsbdSecPatch**](https://github.com/InvoxiPlayGames/UsbdSecPatch) for Xbox 360, or select the patch in J-Runner while flashing your NAND)
- Playstation Classic
- DInput

## 变更平台
By default the OGX-Mini will emulate an OG Xbox controller, you must hold a button combo for 3 seconds to change which platform you want to play on. Your chosen mode will persist after powering off the device. 

默认情况下手柄转换器将模拟初代XBOX手柄，你需要按下下列任一组合键来切换使用平台。切换平台后手柄断开连接不会受到影响。

Start = Plus (Switch) = Options (Dualsense/DS4)

开始键=加号(NS)=OPTION（PS4/PS5)

- XInput
    - 开始键 + 方向键上
- 初代 Xbox
    - 开始键 + 方向键右
- 初代 XBOX 铁骑控制器
    - 开始键 + 方向键右 + 右肩键
- 初代 XBOX DVD 遥控器
    - 开始键 + 方向键右 + 左肩键
- Switch
    - 开始键 + 方向键下
- PlayStation 3
    - 开始键 + 方向键左
- PlayStation Classic
    - 开始键 + A (PS系手柄为X，任天堂系手柄按B)
- 网页配置模式
    - 开始键 + 左肩键 + 右肩键


切换模式后，转换器将自动重启，无需重新拔插。


## 支持的设备
### 有线手柄
- 初代 XBOX 公爵手柄和S手柄
- XBOX 360/ONE/SERIES/精英手柄
- Dualshock 3 (PS3)
- Dualshock 4 (PS4)
- Dualsense (PS5)
- Nintendo Switch Pro
- Nintendo Switch wired
- Nintendo 64 Generic USB
- Playstation Classic
- 常规 DInput 手柄
- 常规 HID 手柄 (可能需要去网页配置模式修改按键映射)

Note: There are some third party controllers that can change their VID/PID, these might not work correctly.

注意：部分第三方手柄可能无法正常使用。

### 无线适配器
- XBOX360 PC适配器 (微软官方或克隆)
- 八位堂v1和v2蓝牙适配器 (设置为 XINPUT 模式)
- 绝大多数支持 Switch/PS/XINPUT 模式的无线手柄接收器

### Wireless Bluetooth controllers (Pico W & ESP32)
**Note:** Bluetooth functionality is in early testing, some may have quirks.
- Xbox Series, One, and Elite 2
- Dualshock 3
- Dualshock 4
- Dualsense
- Switch Pro
- Steam
- Stadia
- And more

Please visit [**this page**](https://bluepad32.readthedocs.io/en/latest/supported_gamepads/) for a more comprehensive list of supported controllers and Bluetooth pairing instructions.

## Features new to v1.0.0
- Bluetooth functionality for the Pico W, Pico 2 W, and Pico+ESP32.
- Web application (connectable via USB or Bluetooth) for configuring deadzones and buttons mappings, supports up to 8 saved profiles.
- Pi Pico 2 and Pico 2 W (RP2350) support.
- Reduced latency by about 3-4 ms, graphs showing comparisons are coming.
- 4 channel functionality, connect 4 Picos and use one Xbox 360 wireless adapter to control all 4.
- Delayed USB mount until a controller is plugged in, useful for internal installation (non-Bluetooth boards only). 
- Generic HID controller support.
- Dualshock 3 emulation (minus gyros), rumble now works.
- Steel Battalion controller emulation with a wireless Xbox 360 chatpad.
- Xbox DVD dongle emulation. You must provide or dump your own dongle firmware, see the Tools directory.
- Analog button support on OG Xbox and PS3.
- RGB LED support for RP2040-Zero and Adafruit Feather boards.

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
