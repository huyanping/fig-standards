Basic Coding Standard
=====================

��������淶
=====================

This section of the standard comprises what should be considered the standard
coding elements that are required to ensure a high level of technical
interoperability between shared PHP code.

�������ǽ�������һЩ�����Ĵ���淶���⣬
�Դ���Ϊ�������۸��߼���Ĵ������ͼ������õĻ�����

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119].

[RFC 2119] �еı���(MUST)������(MUST NOT)��
����(SHOULD)��������(SHOULD NOT)������/����(MAY)�ȹؼ���
���ڱ���������һЩ�����Ե�������

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[PSR-4]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-4-autoloader.md


1. Overview
-----------

1. ����
-----------

- Files MUST use only `<?php` and `<?=` tags.

- �ļ�����ֻʹ�� `<?php` �� `<?=` �����ֱ�ǩ��

- Files MUST use only UTF-8 without BOM for PHP code.

- �ļ���php����ı����ʽ����ֻʹ����BOMͷ��UTF-8��

- Files SHOULD *either* declare symbols (classes, functions, constants, etc.)
  *or* cause side-effects (e.g. generate output, change .ini settings, etc.)
  but SHOULD NOT do both.

- һ���ļ�����ֻ��������������(class)������(function)������(constant)�ȣ�
����ֻ������һЩ�������õĲ��������磺�����Ϣ���޸�.ini���õȣ���
��������ͬʱ���������¡�

- Namespaces and classes MUST follow an "autoloading" PSR: [[PSR-0], [PSR-4]].

- �����ռ�(namespace)����(class) ��������PSR-0��׼��

- Class names MUST be declared in `StudlyCaps`.

- ��������ʹ�� `StudlyCaps` д�� (����ע��StudlyCapsΪ���շ壬���Ľ�ֱ����StudlyCaps��ʾ)��

- Class constants MUST be declared in all upper case with underscore separators.

- ���еĳ�������ֻ�ɴ�д��ĸ���»���(_)��ɡ�

- Method names MUST be declared in `camelCase`.

- ����������ʹ�� `cameCase` д��(����ע��cameCaseΪС�շ壬���Ľ�ֱ����camelCase��ʾ)��


2. Files
--------

2. �ļ�
--------

### 2.1. PHP Tags

### 2.1. PHP��ǩ

PHP code MUST use the long `<?php ?>` tags or the short-echo `<?= ?>` tags; it
MUST NOT use the other tag variations.

PHP�������ֻʹ�ó���ǩ(<?php ?>)���߶����ʽ��ǩ(<?= ?>)��
������ʹ��������ǩ��

### 2.2. Character Encoding

### 2.2. �ַ�����

PHP code MUST use only UTF-8 without BOM.

PHP����ı����ʽ����ֻʹ����BOMͷ��UTF-8��

### 2.3. Side Effects

### 2.3. ������

A file SHOULD declare new symbols (classes, functions, constants,
etc.) and cause no other side effects, or it SHOULD execute logic with side
effects, but SHOULD NOT do both.

һ��Դ�ļ�����ֻ��������������(class)������(function)������(constant)�ȣ�
����ֻ������һЩ�������õĲ��������磺�����Ϣ���޸�.ini���õȣ���
��������ͬʱ���������¡�

The phrase "side effects" means execution of logic not directly related to
declaring classes, functions, constants, etc., *merely from including the
file*.

���︱���õ���˼���ڰ����ļ�ʱ��ִ�е��߼�
������������(class)������(function)������(constant)��û��ֱ�ӵĹ�ϵ��

"Side effects" include but are not limited to: generating output, explicit
use of `require` or `include`, connecting to external services, modifying ini
settings, emitting errors or exceptions, modifying global or static variables,
reading from or writing to a file, and so on.

�����ð������������ڣ������������ʽ��ʹ��require��include��
�����ⲿ�����޸�ini���ã�����������쳣���޸�ȫ�ֻ��߾�̬������
��ȡ���޸��ļ��ȵȡ�

The following is an example of a file with both declarations and side effects;
i.e, an example of what to avoid:

������һ���Ȱ����������и����õ�ʾ���ļ�����Ӧ��������ӣ�

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

```php
<?php
// ������: �޸���ini����
ini_set('error_reporting', E_ALL);

// side effect: �������ļ�
include "file.php";

// side effect: ���������
echo "<html>\n";

// ����
function foo()
{
    // ������
}
```

The following example is of a file that contains declarations without side
effects; i.e., an example of what to emulate:

������һ��������������ʾ���ļ�����Ӧ�ᳫ�����ӣ�

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


```php
<?php
// ����
function foo()
{
    // ������
}

// ����ʽ�����������Ǹ�����
if (! function_exists('bar')) {
    function bar()
    {
        // ������
    }
}
```


3. Namespace and Class Names
----------------------------

3. �����ռ� �� ����
----------------------------

Namespaces and classes MUST follow [PSR-0].

�����ռ����������� [PSR-0]��

This means each class is in a file by itself, and is in a namespace of at
least one level: a top-level vendor name.

����ζ��һ��Դ�ļ���ֻ����һ����(class)��
����ÿ��������Ҫ��һ���ռ�������һ����������֯����

Class names MUST be declared in `StudlyCaps`.

��������ʹ�� `StudlyCaps` д����

Code written for PHP 5.3 and after MUST use formal namespaces.

PHP5.3֮��Ĵ������ʹ����ʽ�������ռ䡣

For example:

ʾ����

```php
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```

Code written for 5.2.x and before SHOULD use the pseudo-namespacing convention
of `Vendor_` prefixes on class names.

PHP5.2.x֮ǰ�Ĵ��뽨����α�����ռ� `Vendor_` ��Ϊ���ǰ׺

```php
<?php
// PHP 5.2.x and earlier:
class Vendor_Model_Foo
{
}
```

4. Class Constants, Properties, and Methods
-------------------------------------------

4. ��ĳ��������ԣ��ͷ���
-------------------------------------------

The term "class" refers to all classes, interfaces, and traits.

����ࡱָ�ࣨclass�����ӿڣ�interface������ ���ԣ�traits����

### 4.1. Constants

### 4.1. ����

Class constants MUST be declared in all upper case with underscore separators.

�ೣ������ֻ�ɴ�д��ĸ���»�����ɡ�

For example:

ʾ����

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

### 4.2. Properties

### 4.2 ����

This guide intentionally avoids any recommendation regarding the use of
`$StudlyCaps`, `$camelCase`, or `$under_score` property names.

��ָ���й��ⲻ�� `$StulyCaps`��`$camelCase`
���� `$unser_score` �е�ĳһ�ַ�����ر��Ƽ���
��ȫ�ɶ������ݸ���ϲ�þ������������������

Whatever naming convention is used SHOULD be applied consistently within a
reasonable scope. That scope may be vendor-level, package-level, class-level,
or method-level.

���ǲ�������ζ�����������������һ������ķ�Χ�ڱ���һ�¡�
�����Χ��������֯����ģ�������ģ��༶��ģ����߷�������ġ�

### 4.3. Methods

### 4.3 ����

Method names MUST be declared in `camelCase()`.

�����������ʹ�� `camelCase()` �����������