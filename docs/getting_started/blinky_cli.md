# Blinky on mbed CLI

## Quick start video

<span class="images">[![Video tutorial](http://img.youtube.com/vi/EAZGws9xUSI/0.jpg)](http://www.youtube.com/watch?v=EAZGws9xUSI)</span>

## Installing mbed CLI and a toolchain

mbed CLI is an offline tool, meaning you'll have to install it before you can work. You will also need to install a toolchain. Please follow the installation instructions on the [mbed CLI page](../dev_tools/cli.md), and come back here when you're done.

## Setting context

Whenever you work with mbed CLI, you need to navigate your command-line terminal to the directory it which you want to work. For example, if your program is in a folder called ``my_program``:

```
cd my_program
mbed <commands>
```

## Get Blinky

mbed CLI can import Blinky, along with the mbed OS codebase. The import process creates a new directory as a subdirectory of you current context (as explained above). 

To import Blinky, from the command line:

1. Navigate to a directory of your choice. We're navigating to our development directory:

    ``cd dev_directory``

1. Import the example:

    ```
    mbed import mbed-os-example-blinky
    cd mbed-os-example-blinky
    ```

Blinky is now under ``dev_directory`` > `` mbed-os-example-blinky``. You can look at ``main.cpp`` to familiarize yourself with the code.

## Compile

Invoke `mbed compile`, specifying:

* Your board: ``-m <board_name>``
* Your toolchain ``-t <GCC_ARM`, `ARM` or `IAR`>``.

For example, for the board K64F and the ARM Compiler 5:

```
mbed compile -m K64F -t ARM
```

Your PC may take a few minutes to compile your code. At the end you should get the following result:

```
[snip]
+----------------------------+-------+-------+------+
| Module                     | .text | .data | .bss |
+----------------------------+-------+-------+------+
| Misc                       | 13939 |    24 | 1372 |
| core/hal                   | 16993 |    96 |  296 |
| core/rtos                  |  7384 |    92 | 4204 |
| features/FEATURE_IPV4      |    80 |     0 |  176 |
| frameworks/greentea-client |  1830 |    60 |   44 |
| frameworks/utest           |  2392 |   512 |  292 |
| Subtotals                  | 42618 |   784 | 6384 |
+----------------------------+-------+-------+------+
Allocated Heap: unknown
Allocated Stack: unknown
Total Static RAM memory (data + bss): 7168 bytes
Total RAM memory (data + bss + heap + stack): 7168 bytes
Total Flash memory (text + data + misc): 43402 bytes
Image: .\.build\K64F\ARM\mbed-os-example-blinky.bin             
```

The program file, ``mbed-os-example-blinky.bin``, is under your ``build\K64F\ARM\`` folder.

## Program your board

mbed enabled boards are programable by drag and drop over a USB connection.

1. Connect your mbed board to the computer over USB.
1. Copy the binary file to the board. In the example above, the file is ``mbed-os-example-blinky.bin``, and it's under the ``build\K64F\ARM\`` folder.
1. Press the reset button to start the program.

You should see the LED of your board turning on and off.