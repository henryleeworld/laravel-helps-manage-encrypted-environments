# Laravel 12 幫助管理加密環境設定

引入 intermax 的 veil 套件來擴增幫助管理加密環境設定，加密環境設定會將整個檔案內容轉換成單一加密字串。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __env:encrypt__ 指令來加密環境設定。
```sh
$ php artisan env:encrypt --only-values {--all|--only="第一個環境變數,..."}
```
- 執行 __env:decrypt__ 指令來解密環境設定。
```sh
$ php artisan env:decrypt --only-values --key {金鑰} --cipher {加密演算法}
```

----

## 畫面截圖
![](https://i.imgur.com/SQ3BXlF.png)
> 將人類可讀的純文字轉換為不可理解文字，並提供金鑰和加密演算法以供解密

![](https://i.imgur.com/zasgtnh.png)
> 解密時保持未加密的設定不變
