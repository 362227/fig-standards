編碼風格文件
==================

這份文件(PSR-2)從[PSR-1][]([PSR-1 翻譯][])這份基本編碼標準所延伸、擴充 。

本文件希望能藉由一套共用的規則讓大家可以格式化 PHP 程式，以期降低大家在看各作者間程式碼時，因風格的不同所造成的衝擊。

此處的風格規則由不同專案的成員所合作。各成員彼此合作於多個專案間，而這份指導方針讓他們使用在各個專案間。因此，這份文件的優點就是沒有規則，而唯一的規則就是分享。

在文件中所使用到的關鍵字 “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, 以及 “OPTIONAL” 皆引用自 [RFC 2119][] 中說明。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[PSR-1 翻譯]: https://github.com/mosil/fig-standards/blob/patch-1/accepted/PSR-1-basic-coding-standard.md

1. 總覽
-----------

- 程式碼一定 (MUST) 得依循 [PSR-1][]([PSR-1 翻譯][]).

- 程式碼的縮排一定 (MUST) 是用四個空白，而非 tab。

- 每行的字數長度需 (SHOLD) 得少於 80 字元；一定 (MUST) 要將相對限制(soft limit) 設定在 120 字元；必不要 (MUST NOT) 寫到絕對限制 (hard limit)。

- 宣告 `命名空間 (namespace)` 之下一定(MUST) 要空一行，以及宣告 `use` 之下一定 (MUST) 也要空一行。

- 類別 (class) 所使用的成對花括號，一定(MUST) 要將開始的放在宣告的下一行，以及程式碼本體結束的下一行。

- 方法 (method) 所使用的成對花括號，一定(MUST) 要將開始的放在宣告的下一行，以及程式碼本體結束的下一行。

- 所有屬性或是方法的可視屬性(visibility)一定(MUST) 要宣告， `abstract` 以及 `final` 一定(MUST) 是宣告在可視屬性之前； `static` 則一定(MUST) 是宣告在可視屬性之後。
  
- 控制結構 (control structure) 的關鍵字一定(MUST) 要在其後加入一個空白；方法(Method) 與函式(Function)則一定不要(MUST NOT)。

- 控制結構的開始(左)花括號一定(MUST) 要在宣告啟始的同一行，而結束(右)花括號則一定(MUST) 要在其程式碼本體結束的下一行。

- 控制結構中，用到括弧時，其開始(左)括弧之後與結束(右)括弧之前一定不要(MUST NOT) 有空白。

### 1.1 範例

下面這個範例包含一些總覽中的規則：

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

2. 通則
----------

### 2.1 基本編碼標準

程式碼一定 (MUST) 要依循 [PSR-1][]([PSR-1 翻譯][]) 的說明。

### 2.2 檔案

所有 PHP 檔案一定(MSUT) 要使用 Unix LF(Line Feed) 做為行的結束。

所有 PHP 檔案在最後結尾處一定(MSUT) 要有一空白行。

在只有 PHP 程式碼的檔案裡，最後一定 (MUST) 不要有結束標籤 `?>`。

### 2.3. 行

每行長度一定不要 (MUST NOT) 用到絕對限制 (hard limit)。

每行的相對限制 (soft limit) 一定 (MUST) 要設定在 120 個字元；自動風格在偵測相對限制時，一定 (MUST) 要設定為警告(warn)，而不要 (MUST NOT) 設定為錯誤(error)。

每行最好不要 (SHOULD NOT) 超過 80 個字元；若是超過，最好(SHOULD) 是拆成多行並維持每行長度 80 字元內。

在非空行的尾端一定不要(MUST NOT) 有空白。

可以 (MAY) 增加空白行增加可讀性，同時可以表達段程式碼是有關連的。

每行一定不要 (MUST NOT) 超過一個敘述 (statement)。

### 2.4 縮排

程式碼的縮排一定 (MUST) 是使用四個空白，而不要 (MUST NOT) 使用跳格做為縮排。

> 備註：只使用空白，不要將空白與 tabs 混用，以避免在散播、補釘、歷史版本以
> 及備註時所發生的問題。而使用空白讓我們在進一步做子縮排時，都很容易地做到
> 對齊的動作。

### 2.5 關鍵字以及 True/False/Null

PHP 的 [關鍵字][] 一定 (MUST) 是小寫。

PHP 的 `true`、`false`以及`null`這幾個常數也一定 (MUST) 是小寫。

[關鍵字]: http://php.net/manual/en/reserved.keywords.php



3. Namespace 與 use 宣告
---------------------------------

當存在時，在宣告 `namespace` 的下一行一定(MUST) 要是空行。

當存在時，所有 `use` 宣告都一定(MUST) 要在 `namespace` 宣告之後。

每個宣告都一定(MUST) 要有關鍵字 `use` 。

在 `use` 區塊之後一定(MUST) 要有一行空行隔開。

範例：

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```


4. 類別、屬性以及函式
-----------------------------------

`class` 一詞包含所有類別、介面以及其所有特性。
> 譯註：[trait][] 在 PHP 5.4 中泛指所有能被重覆使用的函式。

[trait]: http://php.net/manual/en/language.oop5.traits.php

### 4.1 繼承與實作

這 `extends` 以及 `implements` 關鍵字與其類別名稱必需被宣告在同一行。

所使用的成對的大括號之左括號 “{” 一定 (MUST) 是自己獨立一行，而右括號 “}” 也一定 (MUST) 是獨立在程式本體的下一行。

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

而`實作`類別的清單可以 (MAY) 拆開成數行，而緊接在後的每一行皆要縮排。若是要這麼做時，清單中的第一個類別一定 (MUST) 是在宣告的下一行，而每行就是獨立一個介面。

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2 屬性

所以屬性在宣告時一定 (MUST) 要給予初始值。

屬性的宣告一定不能 (MUST NOT) 使用關鍵字 `var` 。

每一次的宣告必不能 (MUST NOT) 超過一個屬性。

屬性若是 protected 或是 private 時，其名稱不需要 (SHOULD NOT) 有個底線做為前置。

一個屬性的宣告方式看起來如下。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3 方法

每個方法的可視屬性(visibility) 一定(MUST) 要宣告。

方法名稱不需要(SHOULD NOT) 在 protected 或是 private 這兩個屬性前加上下底線(“_”)為前置符號。

方法名稱之後一定不要(MUST NOT) 有空白。開始(左)花括號請務必(MUST) 讓他自己存在於一行，且結束(右)花括號也一定(MUST) 要置於程式碼本體之下一行。而開始(左)括弧之後以及結束(右)括弧之前一定不要(MUST NOT) 有空白。

一個方法的宣告可參考下面範例。請注意括弧、逗號、空白以及花括號的位置：

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```    

### 4.4 方法的參數
在參數清單中，每個逗號前一定不要 (MUST NOT) 有空白，而其後一定 (MUST) 要有空白。

方法的參數若是有預設值，則一定(MUST) 要放在參數清單的最後。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

參數清單可以(MAY) 拆開成多行，而每行就是獨立一個參數。若是要這麼做，其第一個參數一定(MUST) 要在宣告的下一行，每行一定(MUST) 只有一個參數。

當參數清單要拆成多行，其結束(右)括弧以及開始(左)花括號一定(MUST) 要在同一行，同時其中間要以空白隔開。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 4.5 abstract、final以及static
當出現 `abstract` 以及 `final` 宣告時，一定(MUST) 要在將之宣告於可視屬性(visbility) 之前。

當出現 `static` 宣告時，一定(MUST) 要將之宣告於可視屬性(visbility) 之後。

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

### 4.6 方法與函式呼叫
當建立一個方法(method)或是函式(function)時，在函式名稱以及開始括弧之間一定不要 (MUST NOT) 有空白，而開始括弧後與結束括弧前也一定不要 (MUST NOT) 有空白。在參數列所用的逗號前一定不要 (MUST NOT) 有空白，而每個逗號後一要 (MUST) 有空白。

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

參數列可以 (MAY) 拆成多行，而每行都縮排。若是要這麼做，第一個參數一定 (MUST) 要再下一行，而且每行就一定 (MUST) 只有一個參數。

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. 控制結構
---------------------

控制結構的通用規則如下：

- 在控制結構的關鍵字之後一定 (MUST) 要用一個空白隔開。
- 在左括弧 “(” 之後一定不要 (MUST NOT) 有空白。
- 在右括弧 “)” 之前一定不要 (MUST NOT) 有空白。
- 在右括弧 “)” 以及開始大(花)括號 ”{“ 之間 一定 (MUST) 要有一個空白隔開。
- 結構本體一定 (MUST) 要有一次縮排。
- 結束的大括號 “}” 一定 (MUST) 要在結構本體的下一行。

每個結構內容都一定 (MUST) 要被包覆在成對的大括號之間。這種標準化看起來會比較有結構，而且可以降低當有新內容要加入主體時錯置的可能性。


### 5.1 `if`, `elseif`, `else`

一個 `if` 結構看起來如下。請注意括弧、空白以及大括號的位置；還有 `else` 以及 `elseif` 跟結束的大括號 “}” 在主體前的同一行裡。

```php
<?php
if ($expr1) {
    // if 主體
} elseif ($expr2) {
    // elseif 主體
} else {
    // else 主體;
}
```

所有 `else if` 這個關鍵字需 (SHOULD) 用 `elseif` 來取代之。

### 5.2 `switch`, `case`

一個 `switch` 結構看起來如下。請注意括號、空白以及大括號的位置。 `case` 敘述一定 (MUST) 要比 `switch` 再縮排一次，而關鍵字 `break` (或其他結束關鍵字) 的縮排層級一定 (MUST) 是同於 `case` 的程式本體。當今天有一個直透非空的 `case` 本體之狀況一定 (MUST) 要註解 // no break 。

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```


### 5.3 `while`, `do while`

一個 `while` 結構看起來如下。請注意括號、空白以及大括號的位置。

```php
<?php
while ($expr) {
    // structure body
}
```

同樣地，一個 `do while` 結構看起來如下。請注意括號、空白以及大括號的位置。

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4 `for`

一個 `for` 敘述看起來如下。請注意括號、空白以及大括號的位置。

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5 `foreach`
    
一個 `foreach` 敘述看起來如下。請注意括號、空白以及大括號的位置。

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6 `try`, `catch`

一個 `try catch` 敘述看起來如下。請注意括號、空白以及大括號的位置。

```php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

6. 閉包
-----------

宣告閉包時一定(MUST) 要有一個空白在 `function` 這個關鍵字之後，以及在關鍵字 `use` 的前後都要有一個空白。

開始(左)花括號一定(MUST)是與其宣告起始在同一行，且結束(右)花括號一定(MUST) 在程式本體結束的下一行。

在開始(左)括弧以及結束(右)括弧與參數或是變數清單之間一定不要(MUST NOT) 有空白。

在參數以及變數清單中的逗號前一定不要(MUST NOT) 有空白，以及逗號之後一定(MUST) 要有一個空白。

閉包中的參數若是有預設值時，一定(MUST) 要放置在參數清單之最後。

閉包的宣告可以參考下面範例。請注意括弧、逗號、空白以及花括號之位置：

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // 程式碼本體
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // 程式碼本體
};
```

參數以及變數清單可以(MAY) 被拆成多行，其每行皆只有獨立一個。當打算這麼做時，清單中的第一個參數/變數一定(MUST) 要在在宣告的下一行，以及每行一定(MUST) 只能有一個參數或變數。

當清單被拆成多行其最後(參數或變數皆是如此)，所使用的結束(右)括弧以及開始(左)花括號一定(MUST) 要在同一行並用空白將二者隔開。

下面是閉包的範例。

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // 程式碼本體
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // 程式碼本體
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // 程式碼本體
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // 程式碼本體
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // 程式碼本體
};
```

請注意若是要在閉包中的參數使用方法 (method) 或是函式 (function) 的格式如下：

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```


7. 總結
--------------

在這份文件中有許多刻意被省略的元素以及做法。這裡僅列出部份：

- 宣告全域變數與全域常數

- 宣告功能

- 運算元與設定值

- 行內的對齊

- 註解以及文件說明區塊

- 類別名稱的前置以及結尾

- 最佳的實作

建議未來可以(MAY) 修改以及擴充這份文件以解決這些或是其他風格以及實作的元素。


附錄 A. 檢視
------------------

這份檢視為撰寫這份風格文件過程中，整個團隊之所有成員在專案中共同決定參照結果。在此留給大家參考。

### A.1 檢視資料

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,http://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
    voting,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,no,no,no,?,yes,no,yes
    indent_type,4,4,4,4,4,tab,4,tab,tab,2,4,tab,4,4,4,4,4,4,tab,tab,4,tab
    line_length_limit_soft,75,75,75,75,no,85,120,120,80,80,80,no,100,80,80,?,?,120,80,120,no,150
    line_length_limit_hard,85,85,85,85,no,no,no,no,100,?,no,no,no,100,100,?,120,120,no,no,no,no
    class_names,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,lower_under,studly,lower,studly,studly,studly,studly,?,studly,studly,studly
    class_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,next,next,next,next,next,next,same,next,next
    constant_names,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper
    true_false_null,lower,lower,lower,lower,lower,lower,lower,lower,lower,upper,lower,lower,lower,upper,lower,lower,lower,lower,lower,upper,lower,lower
    method_names,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,lower_under,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel
    method_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,same,next,next,next,next,next,same,next,next
    control_brace_line,same,same,same,same,same,same,next,same,same,same,same,next,same,same,next,same,same,same,same,same,same,next
    control_space_after,yes,yes,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes
    always_use_control_braces,yes,yes,yes,yes,yes,yes,no,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes
    else_elseif_line,same,same,same,same,same,same,next,same,same,next,same,next,same,next,next,same,same,same,same,same,same,next
    case_break_indent_from_switch,0/1,0/1,0/1,1/2,1/2,1/2,1/2,1/1,1/1,1/2,1/2,1/1,1/2,1/2,1/2,1/2,1/2,1/2,0/1,1/1,1/2,1/2
    function_space_after,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no
    closing_php_tag_required,no,no,no,no,no,no,no,no,yes,no,no,no,no,yes,no,no,no,no,no,yes,no,no
    line_endings,LF,LF,LF,LF,LF,LF,LF,LF,?,LF,?,LF,LF,LF,LF,?,,LF,?,LF,LF,LF
    static_or_visibility_first,static,?,static,either,either,either,visibility,visibility,visibility,either,static,either,?,visibility,?,?,either,either,visibility,visibility,static,?
    control_space_parens,no,no,no,no,no,no,yes,no,no,no,no,no,no,yes,?,no,no,no,no,no,no,no
    blank_line_after_php,no,no,no,no,yes,no,no,no,no,yes,yes,no,no,yes,?,yes,yes,no,yes,no,yes,no
    class_method_control_brace,next/next/same,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/next,same/same/same,same/same/same,same/same/same,same/same/same,next/next/next,next/next/same,next/same/same,next/next/next,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/same,next/next/next

### A.2 檢視說明

`indent_type` : 縮排類型。 `tab` = 使用 tab 鍵一次。 `2` or `4` = 幾個空白鍵。

`line_length_limit_soft` : 相對限制長度的字元數。`?` = 沒有可識別或是無回應。`no` 沒有限制。

`line_length_limit_hard` : 絕對限制長度的字元數。`?` = 沒有可識別或是無回應。`no` 沒有限制。

`class_names` : 類別如何命名。 `lower` = 只能小寫、 `lower_under` = 小寫加底線符號、 `studly` = 大寫開頭之駝峰命名法。

`class_brace_line` : 開始(左)花括號是否和關鍵字 class 在同(`same`)一行，或是在其下(`next`)一行？

`constant_names` : 如何命名常數？ `upper` = 大寫加底線符號。

`true_false_null` : 關鍵字  `true`，`false` 以及 `null` 是否全小寫(`lower`)或全大寫(`upper`)。?

`method_names` : 如何命名方法的名稱？ `camel` = 小寫開頭的駝峰命名法，`lower_under` = 小寫加底線符號。

`method_brace_line` : 開始(左)花括號是否和方法名稱在同(`same`)一行，或是在其下(`next`)一行？

`control_brace_line` : 開始(左)花括號是否和控制結構在同(`same`)一行，或是在其下(`next`)一行？

`control_space_after` : 控制結構關鍵字之後是否要有一個空白？

`always_use_control_braces` : 控制結構是否都要有花括號？

`else_elseif_line` : 用到 `else` 或是 `elseif` 時，前一個敘述的結束(右)花括號是否要在`同一行`，或是在`下一行`？

`case_break_indent_from_switch`: 關鍵字 `case` 與 `break` 與開始的 `switch` 敘述要使用幾次縮排？

`function_space_after` : 在呼叫函式時，其函式名稱以及開始(左)括弧之間是否要有空白？

`closing_php_tag_required` : 在一個僅有 PHP 內容的檔案中，是否需要結束(`?>`)標籤？

`line_endings` : 要以什麼類型做為每行的結束？

`static_or_visibility_first : 在宣告方法時，是要 `static` 在前還是可視屬性在前？
 : 控制結構的表示式其開始(左)括弧之後與結束(右)括弧之前是否要有一個空白？ `yes` = `if ( $expr )`, `no` = `if ($expr)`.

`blank_line_after_php` : 是否有一行空行在 PHP 開始標籤(`<?php`)之後。

`class_method_control_brace`: 彙整開始括號要在類別、方法以及控制結構的哪一行。

### A.3 檢視結果

    indent_type:
        tab: 7
        2: 1
        4: 14
    line_length_limit_soft:
        ?: 2
        no: 3
        75: 4
        80: 6
        85: 1
        100: 1
        120: 4
        150: 1
    line_length_limit_hard:
        ?: 2
        no: 11
        85: 4
        100: 3
        120: 2
    class_names:
        ?: 1
        lower: 1
        lower_under: 1
        studly: 19
    class_brace_line:
        next: 16
        same: 6
    constant_names:
        upper: 22
    true_false_null:
        lower: 19
        upper: 3
    method_names:
        camel: 21
        lower_under: 1
    method_brace_line:
        next: 15
        same: 7
    control_brace_line:
        next: 4
        same: 18
    control_space_after:
        no: 2
        yes: 20
    always_use_control_braces:
        no: 3
        yes: 19
    else_elseif_line:
        next: 6
        same: 16
    case_break_indent_from_switch:
        0/1: 4
        1/1: 4
        1/2: 14
    function_space_after:
        no: 22
    closing_php_tag_required:
        no: 19
        yes: 3
    line_endings:
        ?: 5
        LF: 17
    static_or_visibility_first:
        ?: 5
        either: 7
        static: 4
        visibility: 6
    control_space_parens:
        ?: 1
        no: 19
        yes: 2
    blank_line_after_php:
        ?: 1
        no: 13
        yes: 8
    class_method_control_brace:
        next/next/next: 4
        next/next/same: 11
        next/same/same: 1
        same/same/same: 6


譯者註
--------------
為了讓語句順暢，這邊就不先針對每個字翻譯；而為了維持原文件中之強調性，所以都會將這幾個關鍵字加粗並在其後接上原字，例如一定 (MUST)。