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
3. See [OpenThread CLI Reference README.md][cli] to learn more.

[cli]: https://github.com/openthread/openthread/blob/main/src/cli/README.md

# Contributing

We would love for you to contribute to OpenThread and help make it even better than it is today! See our [Contributing Guidelines](https://github.com/openthread/openthread/blob/main/CONTRIBUTING.md) for more information.

Contributors are required to abide by our [Code of Conduct](https://github.com/openthread/openthread/blob/main/CODE_OF_CONDUCT.md) and [Coding Conventions and Style Guide](https://github.com/openthread/openthread/blob/main/STYLE_GUIDE.md).

# License

OpenThread is released under the [BSD 3-Clause license](https://github.com/openthread/ot-cc2538/blob/main/LICENSE). See the [`LICENSE`](https://github.com/openthread/ot-cc2538/blob/main/LICENSE) file for more information.

Please only use the OpenThread name and marks when accurately referencing this software distribution. Do not use the marks in a way that suggests you are endorsed by or otherwise affiliated with Nest, Google, or The Thread Group.

# Need help?

There are numerous avenues for OpenThread support:

- Bugs and feature requests — [submit to the Issue Tracker](https://github.com/openthread/openthread/issues)
- Stack Overflow — [post questions using the `openthread` tag](http://stackoverflow.com/questions/tagged/openthread)
- Google Groups — [discussion and announcements at openthread-users](https://groups.google.com/forum/#!forum/openthread-users)

The openthread-users Google Group is the recommended place for users to discuss OpenThread and interact directly with the OpenThread team.
