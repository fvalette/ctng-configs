<!--
SPDX-FileCopyrightText: 2026 H2Lab Development Team

SPDX-License-Identifier: Apache-2.0
-->
# ct-ng configs

This repository holds a collection of [crosstool-NG](https://crosstool-ng.github.io/) defconfig files in order to build
cross toolchain for architecture supported by camelot-os.

## How to build

### Using devcontainer

The provided devcontainer.json file provides a ready to build environment w/ required tools and crosstool-NG installed.
Inside the devcontainer:

```console
DEFCONFIG=configs/<triple>.defconfig ct-ng defconfig
[CT_PREFIX=<prefix>] ct-ng build
```

By default, the resulting toolchain is deployed in `<home>/x-tools/<taget-triple>` directory.
If `CT_PREFIX` env var is provided, the path will be `<${CT_PREFIX}>/<target-triple>`.

## Available toolchains

TODO
