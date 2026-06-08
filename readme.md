# HAL_11_DMA_SRAM

## 项目简介

本项目基于 STM32F103xx 系列 MCU，使用 STM32 HAL 库演示 DMA 内存到内存传输，并将传输结果通过 OLED 屏幕显示。
代码由 STM32CubeMX 生成的工程配置为基础，结合自定义 OLED 驱动模块实现显示功能。

## 主要功能

- 初始化 STM32F103 MCU 和 HAL 库
- 通过 DMA 执行 `memtomem` 内存拷贝：`DataA -> DataB`
- 使用 OLED 显示 `DataA` 和 `DataB` 的数值结果
- 展示 MCU 时钟配置、GPIO 初始化、DMA 初始化与轮询传输流程

## 关键文件

- `CMakeLists.txt`：根目录 CMake 构建脚本
- `CMakePresets.json`：CMake 预设配置
- `config.ioc`：STM32CubeMX 项目配置
- `Core/Src/main.c`：主程序入口，执行 DMA 传输和 OLED 显示逻辑
- `Core/Src/OLED.c`：OLED 驱动实现
- `Core/Inc/OLED.h`：OLED 接口声明
- `Core/Inc/OLED_Font.h`：OLED 字库
- `Drivers/STM32F1xx_HAL_Driver/`：STM32 HAL 驱动源代码

## 构建环境与依赖

- CMake
- Ninja 或其他支持的构建生成器
- ARM GCC 交叉编译器，如 `arm-none-eabi-gcc`
- STM32 HAL 库，已包含在 `Drivers/` 目录中

## 构建步骤

```bash
cd d:/Electronics/HAL_Projects/HAL_11_DMA_SRAM
cmake --preset Debug
cmake --build --preset Debug
```

## 运行说明

1. 烧录生成固件到 STM32F103 目标板。
2. 上电后，项目将使用 DMA 把 `DataA` 数据复制到 `DataB`，并在 OLED 上显示这两组数据。

## 硬件说明

- 目标 MCU：STM32F103 系列
- OLED 屏幕接口由项目中的 `OLED.c` 与 `OLED.h` 控制（软件/硬件 I2C 具体引脚请参照项目配置）

## 许可

MIT License
