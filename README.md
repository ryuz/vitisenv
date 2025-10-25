日本語版は[こちら](README_jp.md)

## Overview

A tool for automatically switching versions of Xilinx FPGA development tools (Vitis/Vivado) by directory navigation in Linux environments with multiple versions installed.

## Installation

Install from GitHub:

```bash
git clone https://github.com/ryuz/vitisenv.git ~/.vitisenv
```

Then add the following to your `.bashrc`:

```bash
export VITISENV_ROOT="$HOME/.vitisenv"
export PATH="$VITISENV_ROOT/bin:$PATH"
```

## Usage

First, set the default version:

```bash
vitisenv global 2021.2
```

To automatically switch versions in specific directories:

```bash
vitisenv local 2022.2
```

You can also temporarily switch by setting the VITIS_VERSION environment variable:

```bash
set_vitis 2019.2
```

## Example

Here's how it works:

```bash
$ vitisenv versions
2019.2  2021.2  2022.2
$ vitisenv global 2021.2
$ vitis -version

****** Xilinx Vitis Development Environment
****** Vitis v2021.2.1 (64-bit)
  **** SW Build 3382031 on 2021-12-18-02:29:59
    ** Copyright 1986-2021 Xilinx, Inc. All Rights Reserved.

$ vivado -version
Vivado v2021.2.1 (64-bit)
SW Build 3414424 on Sun Dec 19 10:57:14 MST 2021
IP Build 3405791 on Sun Dec 19 15:54:35 MST 2021
Copyright 1986-2021 Xilinx, Inc. All Rights Reserved.
$ mkdir work
$ cd work
$ vitisenv local 2022.2

****** Xilinx Vitis Development Environment
****** Vitis v2022.2 (64-bit)
  **** SW Build 3671529 on 2022-10-13-17:52:08
    ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.

$ set_vitis 2019.2
$ vitis -version

****** Xilinx Vitis Development Environment
****** Vitis v2019.2.1 (64-bit)
  **** SW Build 2729669 on Thu Dec  5 04:48:51 MST 2019
    ** Copyright 1986-2019 Xilinx, Inc. All Rights Reserved.

$ set_vitis
$ vitis -version

****** Xilinx Vitis Development Environment
****** Vitis v2022.2 (64-bit)
  **** SW Build 3671529 on 2022-10-13-17:52:08
    ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.

$ cd ..
$ vitis -version

****** Xilinx Vitis Development Environment
****** Vitis v2021.2.1 (64-bit)
  **** SW Build 3382031 on 2021-12-18-02:29:59
    ** Copyright 1986-2021 Xilinx, Inc. All Rights Reserved.

```

## Custom Prompt

You can configure your prompt to display the current Vitis version in `.bashrc`.

Here's an example (customize to your preference):

```bash
function parse_vitis_version {
    vitisenv version
}
PS1="[vitis\$(parse_vitis_version)] \u@v\h\w \$ "
```

## License

This project is licensed under the MIT License.