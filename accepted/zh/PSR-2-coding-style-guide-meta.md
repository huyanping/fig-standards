PSR-2 Meta Document
===================

PSR-2 元文档

1. Summary
----------

The intent of this guide is to reduce cognitive friction when scanning code from different authors. It does so 
by enumerating a shared set of rules and expectations about how to format PHP code.

这篇指南的目的是减少阅读不同作者的代码时产生的认知差异。通过枚举一些共享的规则和期望的PHP代码格式。

The style rules herein are derived from commonalities among the various member projects. When various authors 
collaborate across multiple projects, it helps to have one set of guidelines to be used among all those 
projects. Thus, the benefit of this guide is not in the rules themselves, but in the sharing of those rules.

这里所列举的样式规则远不不同成员项目之间的共性。当不同的作者合作开发多个项目时，它有助于为这些项目提供一套指导方针。
因此，本指南的益处并不在于指南本身，而在于分享这些规则。


2. Votes
--------

2. 投票
---------

- **Acceptance Vote:** [ML](https://groups.google.com/d/msg/php-fig/c-QVvnZdMQ0/TdDMdzKFpdIJ)

- **接受投票：**[ML](https://groups.google.com/d/msg/php-fig/c-QVvnZdMQ0/TdDMdzKFpdIJ)


3. Errata
---------

3. 勘误表
---------

### 3.1 - Multi-line Arguments (09/08/2013)

### 3.1 - 多行参数 (09/08/2013)

Using one or more multi-line arguments (i.e: arrays or anonymous functions) does not constitute 
splitting the argument list itself, therefore Section 4.6 is not automatically enforced. Arrays and anonymous 
functions are able to span multiple lines.

使用一行或多行参数（也就是：数组或匿名函数）不会构成参数列表的分裂，因此4.6节是不会自动执行的。
数组和匿名函数是可以跨越多个行的。

The following examples are perfectly valid in PSR-2:

下面的例子在PSR-2中是完全有效的：

```php
<?php
somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) { 
    return 'Hello '.$app->escape($name); 
});
```

### 3.2 - Extending Multiple Interfaces (10/17/2013)

### 3.2 - 扩展多个接口 (10/17/2013)

When extending multiple interfaces, the list of `extends` should be treated the same as a list
of `implements`, as declared in Section 4.1.

当扩展多个接口时，`extends`列表应当与`implements`列表一样同等对待，(ˇ?ˇ) 像4.1描述的那样。
