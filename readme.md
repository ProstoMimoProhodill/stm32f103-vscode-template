# stm32f103 template for VSCode

Tutorial from [Habr](https://habr.com/ru/post/585464/)

## VSCode extensions

- C/C++ by Microsoft
- Makefile Tools by Microsoft
- Cortex-Debug by marus25

## Preparation

It is necessary to install:

- [arm-none-eabi](https://developer.arm.com/downloads/-/gnu-rm)
- openocd

## What was done

1. Debug - Serial Wire (SYS configuration in CubeMX)
2. Toolchain/IDE - Makefile (ProjectManager in CubeMX)
3. Generate code
4. Download SVD file  
   a. Go to [St](https://st.com)  
   b. Products -> Microcontrollers & Microprocessors  
   c. STM32 32-bit Arm Cortex MCUs -> STM32 Mainstream MCUs -> STM32F1 Series -> STM32F103  
   d. Download
5. In Makefile add the next line

```
prog: $(BUILD_DIR)/$(TARGET).elf openocd -f interface/stlink-v2.cfg -f target/stm32f1x.cfg -c "program build/$(TARGET).elf verify exit reset"
```

## Setup settings

In VSCode:

Ctrl+Shift+P -> Preferences: Open User Settings

Find "Cortex"

Open in settings.json

Add the next lines and update paths:

```
"cortex-debug.armToolchainPath": "your path to directory",
"cortex-debug.openocdPath": "your path to file",
"cortex-debug.gdbPath": "your path to file",
```
