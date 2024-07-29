# Devuanのインストールからセットアップまでのメモ

## インストール
最低限のserver.isoを使用してインストール。  
インストーラを起動し、[Install]を選択すればよいが、画面がおかしくなる場合は、
再起動して[Install]をEnterで選択せずTabを押して、vgaオプションを変更する。
  
最低限のもののみインストールし、標準システムユーティリティなどはこの時点ではインストールしない。

## 起動
1) 日本語を選択しても文字化けしているので、`export LANG="C.utf8"`でいったん英語で操作。  
2) suでrootユーザに切り替え、aptでsudoをインストールする。aptでインストールしようとすると、Media Change～と表示されインストールが実行できない。
   なので、/etc/apt/source.listを編集する。その後、apt updateとupgradeを実行。
3) sudoそのままだと使用できないので、/etc/sudoers.dに設定ファイルを置く。
4) 適当にGUI環境を入れる

## amdgpu
AMD Ryzen 5 5600Gを使用しているため、amdgpuをインストールする。  
(注) /etc/apt/sources.listのdeb http://deb.devuan.org/merged daedalus mainのところにnon-free-firmwareを追記してapt updateしないとインストールできない。

## サスペンド、ハイバネーション設定
pm-utilsをインストール。  
★ハイバネーションのために/etc/dafault/grubにswapのUUIDを記載する。

## 音声対応
pulseaudio、pulseaudio-utilsをインストールする。

## 日本語入力対応
fcitx5-mozcをインストールする。
