# Linuxカーネル

## ポイント

### バージョン
1桁目がメジャーバージョン、2桁目がマイナーバージョン、3桁目が安定板のリリース番号

### 確認コマンド

$ uname -[a|r|m]
$ cat /proc/version
$ head /usr/src/kernels/[version]/Makefile

### カーネルモジュール

コマンド
| コマンド名 | 意味 |
| - | - |
| lsmod | ロードされているモジュールをリスト表示 |
| insmod | モジュールをロードする |
| rmmod | モジュールをアンロードする |
| modprobe | 依存関係を解決してモジュールをロードもしくはアンロードする |
| depmod | モジュールの依存関係を更新する |
| modinfo | モジュールの情報を表示する |


### カーネルコンパイル

* ソースを用意する
* .configを設定
* コンパイル
* モジュールをコンパイル
* カーネルとモジュールを配置
* ブートローダの設定変更

コマンド  
$ make 

### カーネルパラメータの設定変更

```
$ sysctl -w [パラメータ]=[値]
```

### 初期RAMディスク

* initrd:ファイルシステムイメージを圧縮したもの、古い
* initramfs:ファイルシステムのドライバが不要、上位互換

$ mkinitrd [RAMディスクイメージファイル] [カーネルパージョン]  
$ mkinitramfs -o [RAMディスクイメージファイル] [カーネルバージョン]

Dracut:udevに対応

### カーネルの管理と問題解決

* /proc  
カーネル内のデータへのインタフェイスとなる特殊なファイルシステム
* コマンド  
  * $ lsdev  
  * $ lspci
  * $ lsusb

### デバイスファイル

* /dev ディレクトリ以下にある、デバイスを抽象化したファイル
  * ブロックデバイス：ファイルタイプb ブロック単位でデバイスにアクセス、HDD,RAM,などボリューム
  * キャラクタデバイス：ファイルタイプc 文字単位でデバイスにアクセス、キーボードやマウスなど、I/O
* /udev
  * あらかじめ /dev 配下に用意する必要があない動的なデバイスファイル管理、ユーザー空間、sysfsが /udev からのアクセスをカーネル空間とつなぐ
  * $ udevadm info  
  * $ udevadm monitor

### study-memo

* カーネルモジュール  
  カーネルモジュールの拡張子は .ko

* sysctl  
  sysctl カーネルパラメータ ⇒ 表示  
  sysctl -w カーネルパラメータ=値 ⇒ 設定  
  sysctl -a ⇒ 一覧表示

/proc/sys/* は、仮想ファイル  
カーネルパラメータが直接記載されている、変更も可能

* initrd.imgをマウント  
  \# mount -o loop initrd.img マウントポイント

* module関連コマンド  
  * lsmod 現在有効になっているモジュールを一覧表示
  * modinfo 指定されたモジュールの情報を表示
  * insmod モジュールを動的にロードする
  * rmmod 指定したロード済みモジュールをアンロード
  * modprobe 依存関係を考慮してモジュールをロード/アンロードする
  * depmod 依存関係ファイル modules.dep を更新する

* bzImage  
  bzImage1はカーネルイメージ（ファイルとして保存されたカーネル本体のデータ）を圧縮し、自己伸長できるようにした形式。bzImageより古いzImageは「512KB以下制限」があった。  
  gzip圧縮で、現在の主に利用されている。

* udev関連コマンド  
  * udevcontrol udevを操作し、動作・停止などを行う
  * udevinfo udevが認識しているデバイス情報を表示する
  * udevmonitor udevの動作状況を監視し、コンソールに出力する
  * udevadm [オプション] 上記のコマンドを統合した新しいコマンド

* カーネルビルド時に登場する主なmakeのオプション
  * 設定関連
  * config 対話的に設定を行う
  * menuconfig ターミナル上のGUIで設定を行う
  * xvonfig X上のGUIで設定を行う
  * defconfig デフォルト状態の設定ファイルを作る
  * oldconfig 現在のカーネルの設定を引き継ぐ
  * cloneconfig (oldconfigと同じ)
  * clean 設定ファイルを除いて一時ファイルなどを削除
  * mrproper 設定ファイルを含めて一時ファイルを削除
  * ビルド関連
  * all カーネルとモジュールをビルド
  * install ビルドしたカーネルをインストール
  * modules カーネルモジュールをビルド
  * modules_install カーネルモジュールをインストール
  * rpm ビルド後にrpmパッケージ化
  * rpm-pkg ソースrpmパッケージを作る
  * binrpm-pkg バイナリ rpm パッケージを作る
  * deb-pkg Debian パッケージを作る 

* カーネルの開発ブランチのカテゴリ
  * prepatch:Release Candidate
  * mainline:prepatch後に出る正式版
  * stable:mainlineの後に出る安定板
  * longterm:stableの中から選ばれ、長期的にサポートされる
