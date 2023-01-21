

# インストール

GitHub から インストール できます。

```
git clone https://github.com/ryuz/vitisenv.git ~/.vitisenv
```

とした後に .bashrc に下記を追加してください。

```
function set_vitis() {
    export VITIS_VERSION=$1
}
export VITISENV_ROOT="$HOME/.vitisenv"
export PATH="$VITISENV_ROOT/bin:$PATH"
```


# 使い方

まず、デフォルトのバージョンを設定します。

```
vitisenv global 2021.2
```

特定のディレクトリ以下で自動でバージョンを切り替えるためには下記のようにします。

```
vitisenv local 2022.2
```

環境変数 VITIS_VERSION を設定することで、一時的に切り替えることも出来ます。

```
set_vitis 2019.2
```


# 例

下記のような動き方をする。

```
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

