# OpenThread on B91 Example

This directory contains example platform drivers for the Telink B91.

The example platform drivers are intended to present the minimal code necessary to support OpenThread. As a result, the example platform drivers do not necessarily highlight the platform's full capabilities.

This platform is intended for exprimentation and exploration of OpenThread, not a production ready environment.

## Build Environment

Building the examples for the b91 requires [CMake][cmake], [Ninja][ninja], and the [Telink risc-v toolchain][telink-toolchain].

[cmake]: https://cmake.org/
[ninja]: https://ninja-build.org/
[telink-toolchain]: http://wiki.telink-semi.cn/tools_and_sdk/Tools/IDE/telink_riscv_linux_toolchain.zip

After these tools are installed, follow the instruction below to install other necessary tools.

```bash
$ cd <path-to-ot-b91>
$ ./script/bootstrap
```

## Building

In a Bash terminal, follow these instructions to build the b91 examples.

```bash
$ cd <path-to-ot-b91>
$ ./script/build
```

## Flash Binaries

If the build completed successfully, the `elf` files may be found in `<path-to-ot-b91>/build/bin`.

You can download the [BDT tool][bdt-tool] and refer to the [user guide][user-guide] provided by Telink to burn the images to the board, in order to load the images with the [BDT tool][bdt-tool], the images must be converted to `bin`. This is done using `riscv32-elf-objcopy`

```bash
$ cd <path-to-ot-b91>/build/bin
$ riscv32-elf-objcopy -S -O binary ot-cli-ftd ot-cli-ftd.bin
```

[bdt-tool]: http://wiki.telink-semi.cn/tools_and_sdk/Tools/BDT/BDT.zip
[user-guide]: http://wiki.telink-semi.cn/tools_and_sdk/Tools/BDT/BDT%20%20User%20Guide.zip

## Interact

### CLI example

1. With a terminal client (putty, minicom, etc.) open the com port associated with the b91 UART. The serial port settings are:
   - 115200 baud
   - 8 data bits
   - no parity bit
   - 1 stop bit
2. Type `help` for a list of commands
3. follow the instructions in the [CLI README][cli-readme] for instructions on setting up a network

[cli-readme]: ./openthread/src/cli/README.md

```bash
> help
help
channel
childtimeout
contextreusedelay
extaddr
extpanid
ipaddr
keysequence
leaderweight
masterkey
mode
netdata register
networkidtimeout
networkname
panid
ping
prefix
releaserouterid
rloc16
route
routerupgradethreshold
scan
start
state
stop
```
