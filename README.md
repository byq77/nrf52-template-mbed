# NRF52 mbed template for Visual Studio Code and MBED CLI

## Web resources

* https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug
* https://marcelball.ca/projects/cortex-debug/
* https://marcelball.ca/projects/cortex-debug/cortex-debug-launch-configurations/
* https://github.com/ARMmbed/mbed-os
* https://github.com/ARMmbed/mbed-os-example-ble
* https://os.mbed.com/docs/mbed-cordio/19.02/introduction/index.html
* https://os.mbed.com/docs/mbed-os/v5.11/apis/bluetooth.html

## Prerequisites
* [Visual Studio Code IDE](https://code.visualstudio.com/)
* [mbed-cli tools](https://os.mbed.com/docs/v5.11/tools/installation-and-setup.html)
* [GNU Arm Embedded version 6 toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)
* [nRF5x Command Line Tools](https://www.nordicsemi.com/DocLib/Content/User_Guides/nrf5x_cltools/latest/UG/cltools/nrf5x_command_line_tools_lpage)

## Setup

1. Create nrf52 workspace

```bash
$ mkdir nrf52-workspace && cd nrf52-workspace
```

2. Import `mbed-os` to the directory

```bash
$ mbed import mbed-os
```

3. Update `mbed-os` to tag `mbed-os-5.13.1`

```bash
$ cd mbed-os
$ mbed update mbed-os-5.13.1
```

4. Create `.mbedignore` in `mbed-os` directory and add:

```
features/cellular/*
features/cryptocell/*
features/deprecated_warnings/*
features/device_key/*
features/FEATURE_BOOTLOADER/*
features/frameworks/*
features/lorawan/*
features/lwipstack/*
features/nanostack/*
features/netsocket/*
features/nfc/*
features/unsupported/*
features/storage/*
components/wifi/*
components/802.15.4_RF/*
components/storage/*
components/TARGET_PSA/*
usb/*
```

5. Set path to mbed-os in Mbed CLI

```bash
$ mbed config -G MBED_OS_DIR <path>/nrf52-workspace/mbed-os
```

6. Import template

```bash
$ git clone https://github.com/byq77/nrf52-template-mbed.git
```

7. Set path to `arm-none-eabi-gcc` in `settings.json`
```json
{
    "C_Cpp.default.compilerPath": "C:\\Program Files (x86)\\GNU Tools ARM Embedded\\6 2017-q2-update\\bin\\arm-none-eabi-gcc.exe",
}
```

## Tasks

To compile/flash:
* `CTRL + SHIFT + P`, type `Tasks: Run Task` and select task.

## Debug

To debug:
* install extension: https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug
* compile and flash DEBUG firmware
* `CTRL + SHIFT + D` and click on `start debug` button


## Mbed Cardio  
Mbed Cardio supports BLE 5.0 features.

To use Mbed Cordio Link Layer instead Nordic SoftDevice in `mbed_app.json` add:
```json
    "target.features_add": ["BLE"],
    "target.extra_labels_add": ["CORDIO", "CORDIO_LL", "SOFTDEVICE_NONE", "NORDIC_CORDIO"],
    "target.extra_labels_remove": ["SOFTDEVICE_COMMON", "SOFTDEVICE_S132_FULL", "NORDIC_SOFTDEVICE"],
```

## DFU bootloader
https://os.mbed.com/users/kord123/notebook/fota-mbed-app-to-nrf52_dk-with-nordic-dfu-boot-loa/

