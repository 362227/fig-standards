基礎編碼標準
=====================

本篇([PSR-1][])將標準化包含了標準編碼元素的部份，以確保高階技術間之 PHP 程式碼的互通性。

在文件中所使用到的關鍵字 “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, 以及 “OPTIONAL” 皆引用自 [RFC 2199][] 中說明。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md


1. 概述
-----------
* 檔案中一定 (MUST) 只能使用 `<?php` 以及 `<?=` 標籤。
* PHP 程式的檔案編碼，一定 (MUST) 要用 “無 BOM 之 UTF-8″ 格式。
* 檔案需要 (SHOULD) 在 宣告 symbols (classes, functions, constants, 等) 或是採用從屬效應(side-effects) (像是產生輸出，變動 .ini 的設定等) 中擇一處理，不需要 (SHOULD NOT) 二者都做。
* 命名空間以及類別一定 (MUST) 依循著 [PSR-0][] 建議文件。
* 類別名稱一定 (MUST) 是採用 大寫開始的 `駝峰大小寫命名法(StudlyCaps)` 來宣告。
* 類別中的宣告常數變數的名稱一定 (MUST) 是由全大寫字母以及底線符號組成。
* 函式名稱一定 (MUST) 是以 小寫開始的 `駝峰大小寫命名法(camelCase)` 宣告。


2. 檔案
--------

### 2.1 PHP 標籤

PHP 程式碼一定要 (MUST) 使用長標籤 `<?php ?>` 或是短標籤 `<?= ?>` ；一定不能使用其它標籤。

### 2.2 字符編碼

PHP程式碼一定要 (MUST) 只使用無 BOM 的 UTF-8 編碼。

### 2.3 從屬效應

一個檔案中所需要 (SHOULD) 的，要嘛就是只宣告新的 symbols (類別、函式以及常數變數等)；不然就是只採用從屬效應(side effects)，就是不需要(SHOULD NOT)二者都在同一個檔案中。

“從屬效應 (Side effects)” 一詞係指在撰寫程式邏輯時，完全只用到引入檔案中的類別、函式或是常數等，而不再自行宣告。

“從屬效應 (Side effects)” 包含 (但還不僅止於此)：產生輸出、明確地使用 `require` 或 `include` 、連接外部的服務、修改 ini 的設定、發出錯誤或例外、更動全域或靜態變數、從檔案讀取或寫入以及諸如此類的動作。

下面這個範例是應該要去避免的情形，一個檔案中包含著宣告以及從屬效應：


```php
<?php
// side effect: change ini settings
ini_set('error_reporting', E_ALL);

// side effect: loads a file
include "file.php";

// side effect: generates output
echo "<html>\n";

// declaration
function foo()
{
    // function body
}
```

再來這個例子是示範一個檔案中沒有從屬效應的宣告方式：

```php
<?php
// declaration
function foo()
{
    // function body
}

// conditional declaration is *not* a side effect
if (! function_exists('bar')) {
    function bar()
    {
        // function body
    }
}
```


3. 命名空間與類別名稱
----------------------------

命名空間以及類別一定要 (MUST) 依循 [PSR-0][]。

這表示每一個類別在該檔案裡，它的命名空間至少要有一層：最上層的提供者名稱(vendor name)。

類別名稱一定要 (MUST) 用 大寫開始的 `駝峰大小寫命名法(StudlyCaps)`。

PHP 5.3 以後的程式碼必需使用正式的命名空間。

舉例來說：


```php
<?php
// PHP 5.3 以後要這麼寫：
namespace Vendor\Model;

class Foo
{
}
```

5.2.x 以前的程式碼，命名類別時需要 (SHOULD) 採用的 `提供者名稱底線 (Vender_)` 方式為開頭的類別名稱之偽命名空間公約。

```php
<?php
// PHP 5.2.x 以前的版本：
class Vendor_Model_Foo
{
}
```

4. 類別裡的常數變數、屬性以及函式
-------------------------------------------

"Class" 一詞包含了所有的類別 (class)、介面 (interfaces)以及特性 (trait)。

### 4.1 常數變數

類別中所宣告的常數變數名稱一定 (MUST) 要由大寫字母以及底線符號所組成。舉例來說：

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

### 4.2 屬性

像這類的命名公約應該 (SHOULD) 是要用在一個合理的範圍裡，而這個範圍應該是在： 提供者層級 (vendor-level)、封包層級 (package-level)、類別層級 (class-level) 或 method-level (函式層)。

因此，本文件故意不對屬性名稱做像是 `駝峰式命名 ($StudlyCaps、$camelCase)` 或是 `底線分隔 ($under_score)` 這樣的命名建議。

### 4.3 函式

函式名稱一定 (MUST) 是採用 小寫開始的 `駝峰大小寫命名法(camelCase())` 宣告。


譯者註
--------------
為了讓語句順暢，這邊就不先針對每個字翻譯；而為了維持原文件中之強調性，所以都會將這幾個關鍵字加粗並在其後接上原字，例如一定 (MUST)。
