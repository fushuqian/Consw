适用于 RP2040 的固件，能够为多种游戏主机模拟游戏手柄。该固件有多种版本，支持 Adafruit Feather USB 主机板、树莓派 Pico、树莓派 Pico 2、树莓派 Pico W、树莓派 Pico 2 W、Waveshare RP2040-Zero、Pico/ESP32 混合板以及 4 通道 RP2040-Zero 配置。
点击此处访问网页应用 以更改按键映射和死区设置。要通过 USB 将 OGX-Mini 与网页应用配对，请插入控制器，然后将其连接到电脑，按住 开始键 + 左 bumper + 右 bumper 进入网页应用模式。在网页应用中点击 “通过 USB 连接” 并选择 OGX-Mini。您也可以通过蓝牙配对，这种情况下无需额外步骤。
支持的平台
初代 Xbox
Playstation 3
Nintendo Switch（底座模式）
XInput（使用 UsbdSecPatch 用于 Xbox 360，或在刷新 NAND 时在 J-Runner 中选择补丁）
Playstation Classic
DInput
切换平台
默认情况下，OGX-Mini 将模拟初代 Xbox 控制器，您必须按住按钮组合 3 秒钟才能更改要使用的平台。选择的模式在设备断电后仍会保留。
开始键 = 加号（Switch）= 选项键（Dualsense/DS4）
XInput
开始键 + 方向键上
初代 Xbox
开始键 + 方向键右
初代 Xbox 铁骑控制器
开始键 + 方向键右 + 右肩键
初代 Xbox DVD 遥控器
开始键 + 方向键右 + 左肩键
Switch
开始键 + 方向键下
PlayStation 3
开始键 + 方向键左
PlayStation Classic
开始键 + A（PS 系手柄为 X，任天堂系手柄按 B）
网页配置模式
开始键 + 左肩键 + 右肩键
切换模式后，转换器将自动重启，无需重新拔插。
支持的设备
有线手柄
初代 Xbox 公爵手柄和 S 手柄
XBOX 360/ONE/SERIES/ 精英手柄
Dualshock 3（PS3）
Dualshock 4（PS4）
Dualsense（PS5）
Nintendo Switch Pro
Nintendo Switch 有线手柄
Nintendo 64 通用 USB 手柄
Playstation Classic 手柄
常规 DInput 手柄
常规 HID 手柄（可能需要在网页配置模式下修改按键映射）
注意：有些第三方控制器可以更改其 VID/PID，这些可能无法正常工作。
无线适配器
XBOX360 PC 适配器（微软官方或克隆版）
八位堂 v1 和 v2 蓝牙适配器（设置为 XINPUT 模式）
绝大多数支持 Switch/PS/XINPUT 模式的无线手柄接收器
无线蓝牙控制器（Pico W 和 ESP32）
注意： 蓝牙功能处于早期测试阶段，可能存在一些问题。
Xbox Series、One 和 Elite 2 手柄
Dualshock 3 手柄
Dualshock 4 手柄
Dualsense 手柄
Switch Pro 手柄
Steam 手柄
Stadia 手柄
以及更多
有关支持的控制器的更全面列表和蓝牙配对说明，请访问 此页面。
v1.0.0 的新功能
为 Pico W、Pico 2 W 和 Pico+ESP32 提供蓝牙功能。
网页应用（可通过 USB 或蓝牙连接），用于配置死区和按键映射，支持最多 8 个保存的配置文件。
支持树莓派 Pico 2 和 Pico 2 W（RP2350）。
延迟降低约 3-4 毫秒，比较图表即将推出。
4 通道功能，连接 4 个 Pico 并使用一个 Xbox 360 无线适配器来控制所有 4 个。
延迟 USB 挂载直到插入控制器，这对内部安装很有用（仅非蓝牙板）。
支持通用 HID 控制器。
模拟 Dualshock 3（不含陀螺仪），震动功能现在可用。
用无线 Xbox 360 聊天板模拟 Steel Battalion 控制器。
模拟 Xbox DVD 加密狗。您必须提供或转储自己的加密狗固件，请参阅工具目录。
在初代 Xbox 和 PS3 上支持模拟按钮。
为 RP2040-Zero 和 Adafruit Feather 板提供 RGB LED 支持。
计划添加的功能
为未知 HID 控制器提供更准确的报告解析器
用于初代 Xbox 内部安装的硬件设计
4 通道 RP2040-Zero 适配器的硬件设计
有线 Xbox 360 聊天板支持
有线 Xbox One 聊天板支持
Switch（作为输入）震动支持
某种形式的初代 Xbox 通信器支持
通用蓝牙加密狗支持
按钮宏
震动设置（强度、启用 / 禁用等）
硬件
有关 Pi Pico、RP2040-Zero、4 通道和 ESP32 配置，请参阅硬件文件夹中的图表。
我为 RP2040-Zero 设计了一块 PCB，这样您就可以自己制作一个小尺寸的适配器。Gerber 文件、原理图和物料清单在硬件文件夹中。
<img src="images/OGX-Mini-rpzero-int.jpg" alt="OGX-Mini 开发板" width="400">
如果您想要一个预构建的单元，可以从我的 Etsy 商店 购买，包括电缆和 Xbox 适配器。
添加支持的控制器
如果您的第三方控制器无法工作，但上面列出了原始版本，请将设备的 VID 和 PID 发送给我，我会添加它以便正确识别。
构建
RP2040
您可以在配置项目时使用 CMake 参数 OGXM_BOARD 为不同的开发板编译此固件。
选项包括：
PI_PICO
PI_PICO2
PI_PICOW
PI_PICO2W
RP_ZERO
ADA_FEATHER
PICO_ESP32
EXTERNAL_4CH
您还可以设置 MAX_GAMEPADS，如果大于 1，则仅支持 DInput（PS3）和 Switch。
您需要安装 git、python3、CMake、Ninja 和 GCC ARM 工具链。CMake 脚本将修补 Bluepad32 和 BTStack 中的一些文件，并确保所有 git 子模块（及其子模块和依赖项）都已下载。以下是 Windows 上的示例：
plaintext
git clone --recursive https://github.com/wiredopposite/OGX-Mini.git
cd OGX-Mini/Firmware/RP2040
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DOGXM_BOARD=PI_PICOW -DMAX_GAMEPADS=1
cmake --build build
或者只需安装 GCC ARM 工具链并在 VSCode 中使用 CMake Tools 扩展。
ESP32
有关将 ESP32 连接到 RP2040 的图表，请参阅硬件目录。
您需要安装 ESP-IDF v5.1、esptool、python3 和 git。如果您使用 VSCode，可以安装 ESP-IDF 扩展并为 ESP-IDF v5.1 配置项目，它会为您下载所有内容，然后您只需点击窗口底部的构建按钮。
当您使用 ESP-IDF 构建时，Cmake 将运行一个 python 脚本，将必要的 BTStack 文件复制到组件目录中，这是必需的，因为当您使用 git 下载 BTStack 时，它未被配置为 ESP-IDF 组件。
