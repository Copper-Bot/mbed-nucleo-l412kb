# NUCLEO L412KB - MBED TARGET
This is a target implementation of the NUCLEO L412KB for Mbed framework.

Most of the work has already been done in [mbed-os PR 15215](https://github.com/ARMmbed/mbed-os/pull/15215) and [Giordano_De_Maria post](https://forums.mbed.com/t/nucleo-l412kc-support/16015/9?u=copperbot) post.

Since this board is practically the same has the NUCLEO L432KC, this repository is mainly a copy and paste of what already exists. If working, a PR should be made to add this target to MbedOS.

## Usage
In your project root directory:

1. Add the custom target to your project:

   ```shell
   mbed add https://github.com/Copper-Bot/mbed-nucleo-l412kb.git
   ```

2. Copy the `custom_targets.json` at the root of the project.

3. Set the new target:

   ```shell
   mbed target NUCLEO_L412KB
   ```

## Upload

Since this board is not yet present in [mbed-os database](https://github.com/ARMmbed/mbed-os-tools/blob/master/src/mbed_os_tools/detect/platform_database.py), it must be added for `mbed compile --flash` command to work.

In the root of your project, type the two following commands:

```shell
pip install mbed-ls --upgrade
mbedls --mock 0846:NUCLEO_L412KB
```

This should add the board in your local database.

## Infos

- Is `"device_name": "STM32L412KBTx"` same has `"device_name": "STM32L412KBUx"` ?
  Has explained [here](https://forums.mbed.com/t/nucleo-l412kc-support/16015/14), `"STM32L412KBUx"` does not exist. But judging by [ST datasheet](https://www.st.com/resource/en/datasheet/stm32l412kb.pdf), it's just a change of package, so same pinout, same chip inside.
- removed peripherals : DAC, SPI3, CAN, SAI
- PLL  P parameter does not exist on L412KB target.
- USB has been enabled by default for Mbed.
- USB may work only in MSI mode, since it is his only source. This is an issue.
