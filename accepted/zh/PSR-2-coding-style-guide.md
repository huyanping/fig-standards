Coding Style Guide
==================

������ָ��
==================

This guide extends and expands on [PSR-1], the basic coding standard.

��ָ���ڻ��������׼ [PSR-1] ֮�Ͻ����������չ��

The intent of this guide is to reduce cognitive friction when scanning code
from different authors. It does so by enumerating a shared set of rules and
expectations about how to format PHP code.

��ָ�ϵ���ͼ�����������Ķ���ͬ�����ߴ����Ч�ʡ�
�����о���һЩ�й���θ�ʽ��PHP����ĳ��ù淶��

The style rules herein are derived from commonalities among the various member
projects. When various authors collaborate across multiple projects, it helps
to have one set of guidelines to be used among all those projects. Thus, the
benefit of this guide is not in the rules themselves, but in the sharing of
those rules.

���������淶�ɸ�����Ŀ֮��Ĺ�����ɡ�
�����������ڶ����Ŀ�к���ʱ������������һ�׹淶��������Щ��Ŀ��ʹ�á�
��ˣ���ָ�ϵ��洦��������Щ��������������������Ŀ�й�����Щ����

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119].

[RFC 2119] �еı���(MUST)������(MUST NOT)��
����(SHOULD)��������(SHOULD NOT)������/����(MAY)�ȹؼ���
���ڱ���������һЩ�����Ե�������

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[PSR-1]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-1-basic-coding-standard.md


1. Overview
-----------

1. ����
-----------

- Code MUST follow a "coding style guide" PSR [[PSR-1]].

- ����������� PSR [[PSR-1]]��

- Code MUST use 4 spaces for indenting, not tabs.

- �������ʹ��4���ո������������������Ʊ����

- There MUST NOT be a hard limit on line length; the soft limit MUST be 120
  characters; lines SHOULD be 80 characters or less.

- һ�д��벻������Ӳ���ƣ������Ʊ���Ϊ120�ַ�������ÿ�д���80���ַ�����١�

- There MUST be one blank line after the `namespace` declaration, and there
  MUST be one blank line after the block of `use` declarations.

- �������ռ� `namespace` ���������������һ�п��У������ڵ��� `use` ����������Ҳ������һ�п��С�

- Opening braces for classes MUST go on the next line, and closing braces MUST
  go on the next line after the body.

- ��������ű���ŵ������������Գ�һ�У��һ����������ŵ������������Գ�һ�С�

- Opening braces for methods MUST go on the next line, and closing braces MUST
  go on the next line after the body.

- �����������ű���ŵ������������Գ�һ�У��һ����������ŵ��������������Գ�һ�С�

- Visibility MUST be declared on all properties and methods; `abstract` and
  `final` MUST be declared before the visibility; `static` MUST be declared
  after the visibility.

- ���е����Ժͷ��������пɼ���������
  `abstract` �� `final` ���������ڿɼ�������֮ǰ��
  `static` ���������ڿɼ�������֮��

- Control structure keywords MUST have one space after them; method and
  function calls MUST NOT.

- �ڿ��ƽṹ�ؼ��ֵĺ��������һ���ո�
  �����ͺ������������治���пո�

- Opening braces for control structures MUST go on the same line, and closing
  braces MUST go on the next line after the body.

- ���ƽṹ�������ű���������ͬһ�У��һ����ű�����ڸÿ��ƽṹ�����������һ�С�

- Opening parentheses for control structures MUST NOT have a space after them,
  and closing parentheses for control structures MUST NOT have a space before.

- ���ƽṹ����Բ����֮�󲻿��пո���Բ����֮ǰҲ�����пո�

### 1.1. Example

### 1.1. ʾ��

This example encompasses some of the rules below as a quick overview:

����ʾ���м�չʾ���������ᵽ��һЩ����

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

2. General
----------

2. ���������淶
----------

### 2.1 Basic Coding Standard

### 2.1 ��������淶

Code MUST follow all rules outlined in [PSR-1].

����������� [PSR-1] �е����й���

### 2.2 Files

### 2.2 �ļ�

All PHP files MUST use the Unix LF (linefeed) line ending.

���е�PHP�ļ�����ʹ�� Unix LF (���з�) ��Ϊ�н�������

All PHP files MUST end with a single blank line.

����PHP�ļ�������һ�����н���

The closing `?>` tag MUST be omitted from files containing only PHP.

��PHP�����ļ��Ĺرձ�ǩ `?>` ����ʡ�ԡ�

### 2.3. Lines

### 2.3. ��

There MUST NOT be a hard limit on line length.

�г��Ȳ�������Ӳ���ơ�

The soft limit on line length MUST be 120 characters; automated style checkers
MUST warn but MUST NOT error at the soft limit.

�г��ȵ������Ʊ�����120�ַ������������ƣ��������������뾯�浫������

Lines SHOULD NOT be longer than 80 characters; lines longer than that SHOULD
be split into multiple subsequent lines of no more than 80 characters each.

һ�д���ĳ��Ȳ����鳬��80���ַ����ϳ����н����ֳɶ��������80���ַ������С�

There MUST NOT be trailing whitespace at the end of non-blank lines.

�ڷǿ��к��治���пո�

Blank lines MAY be added to improve readability and to indicate related
blocks of code.

���п���������ǿ�ɶ��Ժ�������ش���顣

There MUST NOT be more than one statement per line.

һ�в��ɶ���һ����䡣

### 2.4. Indenting

### 2.4. ����

Code MUST use an indent of 4 spaces, and MUST NOT use tabs for indenting.

�������ʹ��4���ո��Ҳ���ʹ���Ʊ������Ϊ������

> N.b.: Using only spaces, and not mixing spaces with tabs, helps to avoid
> problems with diffs, patches, history, and annotations. The use of spaces
> also makes it easy to insert fine-grained sub-indentation for inter-line 
> alignment.

> ע�⣺������ֻʹ�ÿո��Ҳ����Ʊ�����ʹ�ã�
> ����Ա��������죬��������ʷ��ע���е�һЩ�����а�����
> �ո��ʹ�û�����ʹͨ������ϸ΢���������Ľ��м�����ø��ӵļ򵥡�

### 2.5. Keywords and True/False/Null

### 2.5. �ؼ��� �� True/False/Null

PHP [keywords] MUST be in lower case.

PHP [�ؼ���] ����ʹ��Сд��ĸ��

The PHP constants `true`, `false`, and `null` MUST be in lower case.

PHP����  `true`��`false`�� `null` ����ʹ��Сд��ĸ��

[�ؼ���]: http://php.net/manual/en/reserved.keywords.php



3. Namespace and Use Declarations
---------------------------------

3. Namespace �� Use ����
---------------------------------

When present, there MUST be one blank line after the `namespace` declaration.

�����ռ� `namespace` ���������������һ���С�

When present, all `use` declarations MUST go after the `namespace`
declaration.

���е� `use` ����������������ռ� `namespace` ���������档

There MUST be one `use` keyword per declaration.

ÿ�������У�������һ������ `use` �ؼ��֡�

There MUST be one blank line after the `use` block.

�� `use` �����������������һ���С�

For example:

ʾ����

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```


4. Classes, Properties, and Methods
-----------------------------------

4. �࣬���ԣ��ͷ���
-----------------------------------

The term "class" refers to all classes, interfaces, and traits.

����ࡱָ�ࣨclass�����ӿڣ�interface������ ���ԣ�traits����

### 4.1. Extends and Implements

### 4.1. Extends �� Implements

The `extends` and `implements` keywords MUST be declared on the same line as
the class name.

һ����� `extends` �� `implements` �ؼ��ֱ����������ͬ�С�

The opening brace for the class MUST go on its own line; the closing brace
for the class MUST go on the next line after the body.

��������ű�����������Գ�һ�У�
�һ����ű������������ĺ����Գ�һ�С�

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

Lists of `implements` MAY be split across multiple lines, where each
subsequent line is indented once. When doing so, the first item in the list
MUST be on the next line, and there MUST be only one interface per line.

`implements` �б���Ա����Ϊ���������һ�ε����С�
���Ҫ��ɶ�����У��б�ĵ�һ�����Ҫ������һ�У�
����ÿ�б���ֻ��һ���ӿڡ�

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

### 4.2. Properties

### 4.2. ����

Visibility MUST be declared on all properties.

�������Զ�����������ɼ��ԡ�

The `var` keyword MUST NOT be used to declare a property.

`var` �ؼ��ֲ�����������һ�����ԡ�

There MUST NOT be more than one property declared per statement.

ÿ���������ó���һ�����ԡ�

Property names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

���������Ƽ��õ����»�����Ϊǰ׺�������䱣����˽�еĿɼ��ԡ�

A property declaration looks like the following.

һ����������������Ӧ��������������

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Methods

### 4.3. ����

Visibility MUST be declared on all methods.

���еķ���������������ɼ��ԡ�

Method names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

���������Ƽ��õ����»�����Ϊǰ׺�������䱣����˽�еĿɼ��ԡ�

Method names MUST NOT be declared with a space after the method name. The
opening brace MUST go on its own line, and the closing brace MUST go on the
next line following the body. There MUST NOT be a space after the opening
parenthesis, and there MUST NOT be a space before the closing parenthesis.

�����������������治���пո���档
�������ű�����������Գ�һ�У����һ����ű�����ڷ�������������Գ�һ�С�
�����ź��治���пո���������ǰ��Ҳ�����пո�

A method declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

һ��������������Ӧ�������������� ע�����ţ����ţ��ո�ͻ����ŵ�λ�ã�

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

### 4.4. Method Arguments

### 4.4. �����Ĳ���

In the argument list, there MUST NOT be a space before each comma, and there
MUST be one space after each comma.

�ڲ����б��У�����֮ǰ�����пո񣬶�����֮�������Ҫ��һ���ո�

Method arguments with default values MUST go at the end of the argument
list.

��������Ĭ��ֵ�Ĳ���������ڲ����б������档

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

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

�����б���Ա����Ϊ���������һ�ε����С�
���Ҫ��ֳɶ�����У�
�����б�ĵ�һ����������һ�У�
����ÿ�б���ֻ��һ��������

When the argument list is split across multiple lines, the closing parenthesis
and opening brace MUST be placed together on their own line with one space
between them.

�������б���ֳɶ�����У������ź�������֮�������һ���ո����Գ�һ�С�

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

### 4.5. `abstract`, `final`, and `static`

### 4.5. `abstract`, `final`, �� `static`

When present, the `abstract` and `final` declarations MUST precede the
visibility declaration.

���õ� `abstract` �� `final` ������ʱ�����Ǳ�����ڿɼ���������ǰ�档

When present, the `static` declaration MUST come after the visibility
declaration.

�����õ���̬ `static` ������ʱ���������ڿɼ��������ĺ��档

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

### 4.6. Method and Function Calls

### 4.6. ���÷����ͺ���

When making a method or function call, there MUST NOT be a space between the
method or function name and the opening parenthesis, there MUST NOT be a space
after the opening parenthesis, and there MUST NOT be a space before the
closing parenthesis. In the argument list, there MUST NOT be a space before
each comma, and there MUST be one space after each comma.

����һ����������ʱ���ڷ��������ߺ�������������֮�䲻���пո�
������֮�󲻿��пո�������֮ǰҲ�����пո�
�����б��У�����֮ǰ�����пո񣬶���֮���������һ���ո�

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

�����б���Ա���ֳɶ��������һ�ε����С�
�����ֳ����У��б��еĵ�һ����������һ�У�
����ÿһ�б���ֻ����һ��������

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. Control Structures

5. ���ƽṹ
---------------------

The general style rules for control structures are as follows:

�����Ƕ��ڿ��ƽṹ������ĸ�����

- There MUST be one space after the control structure keyword
- ���ƽṹ�Ĺؼ���֮�������һ���ո�
- There MUST NOT be a space after the opening parenthesis
- ���ƽṹ��������֮�󲻿��пո�
- There MUST NOT be a space before the closing parenthesis
- ���ƽṹ��������֮ǰ�����пո�
- There MUST be one space between the closing parenthesis and the opening
  brace
- ���ƽṹ�������ź�������֮�������һ���ո�
- The structure body MUST be indented once
- ���ƽṹ�Ĵ�������������һ��������
- The closing brace MUST be on the next line after the body
- ���ƽṹ���һ����ű����������һ�С�

The body of each structure MUST be enclosed by braces. This standardizes how
the structures look, and reduces the likelihood of introducing errors as new
lines get added to the body.

ÿ�����ƽṹ�Ĵ���������뱻���ڻ������
��������ʹ���뿴��ȥ���ӱ�׼����
���Ҽ����´����ʱ�򻹿�����˶������������Ŀ����ԡ�


### 5.1. `if`, `elseif`, `else`

An `if` structure looks like the following. Note the placement of parentheses,
spaces, and braces; and that `else` and `elseif` are on the same line as the
closing brace from the earlier body.

������һ�� `if` �������ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�
ͬʱע�� `else` �� `elseif` Ҫ��ǰһ���������ƽṹ���һ�������ͬһ�С�

```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

The keyword `elseif` SHOULD be used instead of `else if` so that all control
keywords look like single words.

�Ƽ��� `elseif` ����� `else if` ���Ա������е��������ƹؼ��ֿ���������һ�����ʡ�


### 5.2. `switch`, `case`

A `switch` structure looks like the following. Note the placement of
parentheses, spaces, and braces. The `case` statement MUST be indented once
from `switch`, and the `break` keyword (or other terminating keyword) MUST be
indented at the same level as the `case` body. There MUST be a comment such as
`// no break` when fall-through is intentional in a non-empty `case` body.

������һ�� `switch` �������ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�
`case` ������Ҫ����һ����
�� `break` �ؼ��֣���������ֹ�ؼ��֣������ `case` �ṹ�Ĵ���������ͬһ�������㼶��
���һ������������ `case` �ṹ����ļ�������ִ�У�
�����Ҫ��һ�������� `// no break` ��ע�͡�

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


### 5.3. `while`, `do while`

A `while` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

������һ�� `while` ѭ�����ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�

```php
<?php
while ($expr) {
    // structure body
}
```

Similarly, a `do while` statement looks like the following. Note the placement
of parentheses, spaces, and braces.

������һ�� `do while` ѭ�����ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

A `for` statement looks like the following. Note the placement of parentheses,
spaces, and braces.

������һ�� `for` ѭ�����ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5. `foreach`
    
A `foreach` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

������һ�� `foreach` ѭ�����ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6. `try`, `catch`

A `try catch` block looks like the following. Note the placement of
parentheses, spaces, and braces.

������һ�� `try catch` �쳣������ƽṹ��ʾ����ע���������ţ��ո�ͻ����ŵ�λ�á�

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

6. Closures
-----------

6. �հ�
-----------

Closures MUST be declared with a space after the `function` keyword, and a
space before and after the `use` keyword.

�����հ�ʱ���õ� `function` �ؼ���֮�����Ҫ��һ���ո�
�� `use` �ؼ��ֵ�ǰ��Ҫ��һ���ո�

The opening brace MUST go on the same line, and the closing brace MUST go on
the next line following the body.

�հ��������ű��������ͬһ�У����һ����ű����ڱհ��������һ�С�

There MUST NOT be a space after the opening parenthesis of the argument list
or variable list, and there MUST NOT be a space before the closing parenthesis
of the argument list or variable list.

�հ��Ĳ����б�ͱ����б�������ź��治���пո������ŵ�ǰ��Ҳ�����пո�

In the argument list and variable list, there MUST NOT be a space before each
comma, and there MUST be one space after each comma.

�հ��Ĳ����б�ͱ����б��ж���ǰ�治���пո񣬶����ź���������пո�

Closure arguments with default values MUST go at the end of the argument
list.

�հ��Ĳ����б��д�Ĭ��ֵ�Ĳ���������ڲ����б�Ľ�β���֡�

A closure declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

������һ���հ���ʾ����ע�����ţ��ո�ͻ����ŵ�λ�á�

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

Argument lists and variable lists MAY be split across multiple lines, where
each subsequent line is indented once. When doing so, the first item in the
list MUST be on the next line, and there MUST be only one argument or variable
per line.

�����б�ͱ����б���Ա���ֳɶ��������һ�������С�
���Ҫ��ֳɶ�����У��б��еĵ�һ����������һ�У�
����ÿһ�б���ֻ��һ�������������

When the ending list (whether or arguments or variables) is split across
multiple lines, the closing parenthesis and opening brace MUST be placed
together on their own line with one space between them.

���б������ǲ������Ǳ��������ձ���ֳɶ�����У�
�����ź�������֮�����Ҫ��һ���ո����Գ�һ�С�

The following are examples of closures with and without argument lists and
variable lists split across multiple lines.

������һ�������б�ͱ����б���ֳɶ�����е�ʾ����

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
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
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

Note that the formatting rules also apply when the closure is used directly
in a function or method call as an argument.

�ѱհ���Ϊһ�������ں������߷����е���ʱ����ȻҪ������������

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


7. Conclusion
--------------

7. �ܽ�
--------------

There are many elements of style and practice intentionally omitted by this
guide. These include but are not limited to:

��ָ�������ʡ�������Ԫ�صĴ�������Ҫ������

- Declaration of global variables and global constants

- ȫ�ֱ�����ȫ�ֳ���������

- Declaration of functions

- ��������

- Operators and assignment

- �������ϸ�ֵ

- Inter-line alignment

- �м����

- Comments and documentation blocks

- ע�ͺ��ĵ���

- Class name prefixes and suffixes

- ������ǰ׺�ͺ�׺

- Best practices

- ���ʵ��

Future recommendations MAY revise and extend this guide to address those or
other elements of style and practice.

�Ժ�Ĵ���淶�п��ܻ���������չ��ָ���й涨�Ĵ�����

Appendix A. Survey
------------------

��¼A ����
------------------

In writing this style guide, the group took a survey of member projects to
determine common practices.  The survey is retained herein for posterity.

Ϊ��д������ָ�ϣ����ǵ����˸�����Ŀ������ȷ��ͨ�õĴ�����
������ε��������﹫��������

### A.1. Survey Data

### A.1. ��������

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

### A.2. Survey Legend

### A.2. ����˵��

`indent_type`:
The type of indenting. `tab` = "Use a tab", `2` or `4` = "number of spaces"

�������͡� `tab` = ��ʹ���Ʊ������`2` or `4` = ���ո�������

`line_length_limit_soft`:
The "soft" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

�г��ȵġ������ƣ����ַ��� `?` = ����ʾ�������֣�`no` ��Ϊ�����ơ�

`line_length_limit_hard`:
The "hard" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

�г��ȵġ�Ӳ�����ƣ����ַ��� `?` = ����ʾ��������, `no` ��Ϊ������.

`class_names`:
How classes are named. `lower` = lowercase only, `lower_under` = lowercase with underscore separators, `studly` = StudlyCase.

����������� `lower` = ֻ��Сд, `lower_under` = Сд���»���, `studly` = ������.

`class_brace_line`:
Does the opening brace for a class go on the `same` line as the class keyword, or on the `next` line after it?

����������Ƿ���ͬһ�л�������һ�У�

`constant_names`:
How are class constants named? `upper` = Uppercase with underscore separators.

�ೣ�����������`upper` = ��д���»��߷ָ�����

`true_false_null`:
Are the `true`, `false`, and `null` keywords spelled as all `lower` case, or all `upper` case?

`true`, `false`, �� `null` �ؼ���ȫ `lower` ���� ȫ `upper`��

`method_names`:
How are methods named? `camel` = `camelCase`, `lower_under` = lowercase with underscore separators.

���������������camel = �շ�ʽ, `lower_under` = Сд���»��߷ָ�����

`method_brace_line`:
Does the opening brace for a method go on the `same` line as the method name, or on the `next` line?

��������������ͬһ�л�������һ�У�

`control_brace_line`:
Does the opening brace for a control structure go on the `same` line, or on the `next` line?

���ƽṹ����������ͬһ�л�������һ�У�

`control_space_after`:
Is there a space after the control structure keyword?

���ƽṹ�ؼ��ʺ��Ƿ��пո�

`always_use_control_braces`:
Do control structures always use braces?

���ƽṹ����ʹ�û����ţ�

`else_elseif_line`:
When using `else` or `elseif`, does it go on the `same` line as the previous closing brace, or does it go on the `next` line?

��ʹ��else��elseif���Ƿ����ͬһ�л�������һ�У�

`case_break_indent_from_switch`:
How many times are `case` and `break` indented from an opening `switch` statement?

case��break�ֱ��swith��䴦�������ٴΣ�

`function_space_after`:
Do function calls have a space after the function name and before the opening parenthesis?

�������õĺ��������������Ƿ��пո�

`closing_php_tag_required`:
In files containing only PHP, is the closing `?>` tag required?

����Ǵ�PHP�ļ����رձ�ǩ?>�Ƿ���Ҫ��

`line_endings`:
What type of line ending is used?

ʹ�ú��ֵ��н�������

`static_or_visibility_first`:
When declaring a method, does `static` come first, or does the visibility come first?

�ڶ��巽����ʱ��static�Ϳɼ���˭��ǰ�棿

`control_space_parens`:
In a control structure expression, is there a space after the opening parenthesis and a space before the closing parenthesis? `yes` = `if ( $expr )`, `no` = `if ($expr)`.

�ڿ��ƽṹ���ʽ�У������ź����������ǰ���Ƿ�Ҫ��һ���ո�yes = if ( $expr ), no = if ($expr).

`blank_line_after_php`:
Is there a blank line after the opening PHP tag?

PHP�Ŀ�ʼ��ǩ�����Ƿ���Ҫһ�����У�

`class_method_control_brace`:
A summary of what line the opening braces go on for classes, methods, and control structures.

���������࣬�����Ϳ��ƽṹ�е�λ�á�

### A.3. Survey Results

### A.3. ������

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