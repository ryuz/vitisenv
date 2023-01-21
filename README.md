## Abstract

This tool is for Linux environments where multiple versions of Vitis/Vivado, Xilinx's FPGA development tool, are installed, so that the version can be automatically switched by moving directories.

## Installation

Install from GitHub

```
git clone https://github.com/ryuz/vitisenv.git ~/.vitisenv
```

Add the following to .bashrc

```
function set_vitis() {
    export VITIS_VERSION=$1
}
export VITISENV_ROOT="$HOME/.vitisenv"
export PATH="$VITISENV_ROOT/bin:$PATH"
```


## Usage

First, set the default version.

```
vitisenv global 2021.2
```

To automatically switch versions of a working directory, do the following.

```
vitisenv local 2022.2
```

It is also possible to switch temporarily by setting the environment variable VITIS_VERSION.

```
set_vitis 2019.2
```

## Exsample

```
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

