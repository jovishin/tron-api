# TRON API 4.0.1 依賴清單

本目錄的 SDK 來自 Orion Base 安裝的 `iexbase/tron-api` 4.0.1，上游提交為 `366227f946f7b8030db8e7326c6f9573c3898583`。SDK 的 PHP 原始碼、測試、範例與 MIT 授權保留自該版本。上游的 Composer 設定原樣保存於 `composer.upstream.json`。每個依賴的完整安裝檔案位於 `dependencies/<套件名稱>/`，版本及提交取自 Orion 的 `composer.lock`。

## 執行期依賴

上游 4.0.1 共有 5 個直接依賴及 12 個間接依賴。下表的引用者僅列出 SDK 的執行期依賴鏈。

| 套件 | 鎖定版本 | 引用者 | 上游提交 |
| --- | --- | --- | --- |
| `comely-io/data-types` | `1.0.34` | `iexbase/tron-api` | [`833ecf364a99`](https://github.com/comely-io/data-types/commit/833ecf364a99aa5cd161e0ebd1191860921834c6) |
| `guzzlehttp/guzzle` | `7.1.1` | `iexbase/tron-api`、`iexbase/web3.php` | [`7427d6f99df4`](https://github.com/guzzle/guzzle/commit/7427d6f99df41cc01f33cd59832f721c150ffdf3) |
| `iexbase/web3.php` | `2.0.1` | `iexbase/tron-api` | [`f25ed954a758`](https://github.com/iexbase/web3.php/commit/f25ed954a7586ead86046dd7e02a333a8098511b) |
| `kornrunner/secp256k1` | `0.1.2` | `iexbase/tron-api` | [`915f0ef1ec74`](https://github.com/kornrunner/php-secp256k1/commit/915f0ef1ec748606a1117b171093266de349b058) |
| `simplito/elliptic-php` | `1.0.9` | `iexbase/tron-api` | [`18a72b837b84`](https://github.com/simplito/elliptic-php/commit/18a72b837b845bf9a2ad2c0050eaf864a22b7550) |
| `fgrosse/phpasn1` | `v2.4.0` | `mdanter/ecc` | [`eef488991d53`](https://github.com/fgrosse/PHPASN1/commit/eef488991d53e58e60c9554b09b1201ca5ba9296) |
| `guzzlehttp/promises` | `v1.3.1` | `guzzlehttp/guzzle` | [`a59da6cf61d8`](https://github.com/guzzle/promises/commit/a59da6cf61d80060647ff4d3eb2c03a2bc694646) |
| `guzzlehttp/psr7` | `1.6.1` | `guzzlehttp/guzzle` | [`239400de7a17`](https://github.com/guzzle/psr7/commit/239400de7a173fe9901b9ac7c06497751f00727a) |
| `kornrunner/keccak` | `1.1.0` | `iexbase/web3.php` | [`433749d28e11`](https://github.com/kornrunner/php-keccak/commit/433749d28e117fb97baf9f2631b92b5d9ab3c890) |
| `mdanter/ecc` | `v0.5.2` | `kornrunner/secp256k1` | [`b95f25cc1bac`](https://github.com/phpecc/phpecc/commit/b95f25cc1bacc83a9f0ccd375900b7cfd343029e) |
| `phpseclib/phpseclib` | `2.0.36` | `iexbase/web3.php` | [`a97547126396`](https://github.com/phpseclib/phpseclib/commit/a97547126396548c224703a267a30af1592be146) |
| `psr/http-client` | `1.0.1` | `guzzlehttp/guzzle` | [`2dfb5f6c5eff`](https://github.com/php-fig/http-client/commit/2dfb5f6c5eff0e91e20e913f8c5452ed95b86621) |
| `psr/http-message` | `1.0.1` | `guzzlehttp/psr7`、`psr/http-client` | [`f6561bf28d52`](https://github.com/php-fig/http-message/commit/f6561bf28d520154e4b0ec72be95418abe6d9363) |
| `ralouphie/getallheaders` | `3.0.3` | `guzzlehttp/psr7` | [`120b605dfeb9`](https://github.com/ralouphie/getallheaders/commit/120b605dfeb996808c31b6477290a714d356e822) |
| `simplito/bigint-wrapper-php` | `1.0.0` | `simplito/bn-php` | [`cf21ec76d33f`](https://github.com/simplito/bigint-wrapper-php/commit/cf21ec76d33f103add487b3eadbd9f5033a25930) |
| `simplito/bn-php` | `1.1.2` | `simplito/elliptic-php` | [`e852fcd27e4a`](https://github.com/simplito/bn-php/commit/e852fcd27e4acbc32459606d7606e45a85e42465) |
| `symfony/polyfill-mbstring` | `v1.38.2` | `kornrunner/keccak` | [`d3d318bad5e7`](https://github.com/symfony/polyfill-mbstring/commit/d3d318bad5e7a1bfbd026009c8bfb8d8f99ae6b6) |

SDK 宣告 PHP `^7.4`。這批套件向 Composer 宣告的擴充套件有 `bcmath`、`gmp`、`iconv`、`json`、`mbstring`。本機 PHP 7.4.33 已載入上述五項擴充，隨附的 `symfony/polyfill-mbstring` 也向 Composer 宣告可提供 `ext-mbstring`。

上游保留 PHPUnit `^6.0` 開發需求與原有測試。Composer 把 SDK 安裝為相依套件時只載入 `require`。本次提取的 17 個套件依此範圍計算。Orion 的 `app/Packages/TronApi` 是應用程式的呼叫端。

## 在本機重現提取版本

在這個目錄搭配 PHP 7.4 執行下列任一條指令。`composer.snapshot.lock` 記錄本機來源的相對路徑與版本。Composer 會從隨附的 17 份原始碼建立 `vendor/autoload.php`，可供本機載入 SDK。第二條指令適用於本機的 MAMP。

```sh
# 適用於已設定 PHP 7.4 的 Composer。
COMPOSER=composer.snapshot.json composer install --no-dev

# 適用於本機 Orion 的 MAMP PHP 7.4.33。
COMPOSER=composer.snapshot.json COMPOSER_MEMORY_LIMIT=512M /Applications/MAMP/bin/php/php7.4.33/bin/php -d memory_limit=512M /Applications/MAMP/bin/php/composer install --no-dev
```

## 從同一個 GitHub 儲存庫安裝

`iexbase/web3.php` 2.0.1 的上游下載網址在驗證時回傳 HTTP 404，Packagist 已凍結該套件。根目錄的 `composer.json` 直接從 `dependencies/iexbase/web3.php/src/` 載入 `Web3\` 命名空間，並宣告提供 `iexbase/web3.php` 2.0.1。它同時列出 Web3 的執行需求，因此使用端可透過同一個儲存庫安裝。 [Packagist 套件狀態](https://packagist.org/packages/iexbase/web3.php)

其他依賴由使用端的 Composer 依版本條件解析。`composer.snapshot.json` 與 `composer.snapshot.lock` 則使用隨附原始碼，適合在本機重現 Orion 當時的 17 個版本。

## 發行名稱與路徑

發行用 `composer.json` 與本機重現用 `composer.snapshot.json` 使用 `jovishin/tron-api`。上游名稱、設定與著作權聲明保存在 `composer.upstream.json`、`README.upstream.md` 及 `LICENSE`。發行用設定向 Composer 宣告取代 `iexbase/tron-api` 4.0.1，讓既有應用程式可切換套件並沿用 `IEXBase\TronAPI\` 與 `Web3\`。

上傳目錄結構、`v4.0.1` 標籤、首次安裝與正式主機部署指令列在 [README.md](README.md)。

這個版本透過 `kornrunner/secp256k1` 依賴 `mdanter/ecc ^0.5`。此範圍受 CVE-2024-33851 影響。啟用預設安全封鎖的 Composer 從 Packagist 全新解析時，可能拒絕安裝。此次保留 Orion 鎖定的版本供重現。 [安全公告](https://github.com/advisories/GHSA-3494-cfwf-56hw) · [Composer 安全政策](https://getcomposer.org/doc/06-config.md#block-insecure)
