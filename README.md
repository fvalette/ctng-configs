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

#### Build a defconfig

```console
DEFCONFIG=configs/<triple>.defconfig ct-ng defconfig
[CT_PREFIX=<prefix>] ct-ng build
```

By default, the resulting toolchain is deployed in `<home>/x-tools/<taget-triple>` directory.
If `CT_PREFIX` env var is provided, the path will be `<${CT_PREFIX}>/<target-triple>`.

#### Generate SBOM

`support/generate-sbom` use `ct-ng show-config` command and build log to collect information in
order to produce Software Bill of Materials (SBOM) in SPDX or CycloneDX json format.
Indise the devcontainer, one could use the following command to display the sbom in stdout (need to
build the toolchain before).

```console
support/generate-sbom --help
usage: generate-sbom [-h] --format FORMAT [--show-config FILE] [--build-log FILE] [--ctng-dir DIR] [--output FILE] [--toolchain-name NAME]

Generate an SBOM for a crosstool-NG toolchain.

options:
  -h, --help            show this help message and exit
  --format FORMAT       Output format: 'spdx' (SPDX 2.3 JSON) or 'cyclonedx' (CycloneDX 1.6 JSON)
  --show-config FILE    Path to ct-ng show-config output (default: read from stdin)
  --build-log FILE      Path to the crosstool-NG build log (default: ./build.log)
  --ctng-dir DIR        Path to a crosstool-NG directory containing a packages/ sub-directory
  --output FILE         Write SBOM to FILE instead of stdout
  --toolchain-name NAME
                        Override the toolchain name (default: target triple from show-config)

examples:
  ct-ng show-config | generate-sbom --format spdx
  generate-sbom --format cyclonedx --show-config show-config.txt
  generate-sbom --format spdx --build-log build.log --output toolchain.spdx.json
```

## Available toolchains

TODO
