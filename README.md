# Mac OS Big Sur(11.6.2) - brew upgrade実行時における "cp symlink permission denied / no such file or directory"問題の解決法
個人的備忘録ですので悪しからず

## 実行環境
OS: macOS 11.6.2 20G314 x86_64

Host: MacBookPro12,1 

Kernel: 20.6.0 

## 問題
brew upgradeを実行した際に以下のようなエラーが発生した.(以下一例であり、実際にはこのようなエラーコードが大量に吐き出されてきた)
```
cp: symlink: OPENSSL_malloc.3ssl: No such file or directory
cp: setattrlist: /usr/local/Cellar/openssl/.: Permission denied
```

## 解決法
brew doctorを実行し、指示されるがままに指定されたファイルの削除やプログラムのアップデートを行った。
``` bash
brew doctor
```
次に以下コマンドを実行する
```
sudo chown -R $(whoami) $(brew --prefix)/*
```
これで無事にbrew upgradeを実行できるようになった

> 冒頭でも申しましたが、備忘録レベルです
