# jovishin/tron-api

適用於 PHP 7.4 的 TRON SDK，源自 `iexbase/tron-api` 4.0.1。套件內含 Web3 2.0.1。隨附的依賴版本及來源列在 [DEPENDENCIES.md](DEPENDENCIES.md)。

## 執行條件

使用端需要 PHP 7.4.x，這組依賴宣告的擴充套件包括 `bcmath`、`gmp`、`iconv`、`json` 及 `mbstring`。請以主機的 `php -v` 和 `composer --version` 確認命令列環境。

4.0.1 使用的相依套件 `mdanter/ecc` 0.5.2 受 CVE-2024-33851 影響。Composer 2.9 以上的預設安全政策會阻擋 4.0.1 的全新安裝。 [安全公告](https://github.com/advisories/GHSA-3494-cfwf-56hw) · [Composer 安全政策](https://getcomposer.org/doc/06-config.md#block-insecure)

## 使用 Composer 安裝

在應用程式的根目錄執行下列指令，從 Packagist 安裝套件。

```sh
composer require jovishin/tron-api
```

安裝完成後，可用 `composer show jovishin/tron-api` 確認版本。

## 既有專案切換套件

若應用程式已使用 `iexbase/tron-api` 4.0.1，可在開發或測試環境執行以下指令，切換至 `jovishin/tron-api` 4.0.1。

```sh
# 先換好新舊套件名稱，再一起更新鎖檔。
composer remove iexbase/tron-api --no-update
composer require jovishin/tron-api:4.0.1 --no-update
composer update jovishin/tron-api iexbase/tron-api iexbase/web3.php
composer show jovishin/tron-api
```

這個發行版本向 Composer 宣告可提供上游 SDK 4.0.1 和 Web3 2.0.1。PHP 類別沿用 `IEXBase\TronAPI\` 及 `Web3\` 命名空間，現有的 `use` 可繼續使用。

## 正式主機部署

開發或測試環境確認後，把**應用程式**更新過的 `composer.json` 和 `composer.lock` 一起部署。在正式主機的應用程式根目錄依鎖檔安裝。

```sh
# 使用應用程式已核對的鎖定版本，並檢查實際 PHP 與擴充套件。
composer install --no-dev --prefer-dist --optimize-autoloader --no-interaction
composer check-platform-reqs --no-dev
composer show jovishin/tron-api
```

## 在 PHP 載入

Composer 的預設安裝位置為 `vendor/jovishin/tron-api/`。Laravel 已經載入 Composer，自訂程式可直接使用 `use IEXBase\TronAPI\Tron;`。獨立 PHP 檔若放在應用程式根目錄，可這樣確認地址轉換。

```php
<?php

use IEXBase\TronAPI\Tron;

// 載入應用程式的 Composer，使用已知的公開地址驗證 SDK。
require __DIR__ . '/vendor/autoload.php';

$tron = new Tron();
echo $tron->fromHex('41928c9af0651632157ef27a2cf17ca72c575a4d21');
// 輸出 TPL66VK2gCXNCD7EJg9pgJRfqcRazjhUZY。
```

套件保留上游的 MIT 授權、作者聲明、範例與測試。 [授權](LICENSE) · [範例](examples/)
