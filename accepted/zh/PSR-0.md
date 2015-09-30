Autoloading Standard
====================

�Զ����ر�׼
====================

The following describes the mandatory requirements that must be adhered
to for autoloader interoperability.

������������Ҫʹ��һ��ͨ�õ��Զ���������������Ҫ���صĹ淶��

Mandatory
---------

�淶
---------

* A fully-qualified namespace and class must have the following
  structure `\<Vendor Name>\(<Namespace>\)*<Class Name>`
* һ����ȫ��׼�������ռ����Ľṹ�������ģ�`\<Vendor Name>\(<Namespace>\)*<Class Name>`

* Each namespace must have a top-level namespace ("Vendor Name").
* ÿ�������ռ䶼������һ�������Ŀռ���("��֯��(Vendor Name)")��

* Each namespace can have as many sub-namespaces as it wishes.
* ÿ�������ռ��п��Ը�����Ҫʹ�������������������ռ䡣

* Each namespace separator is converted to a `DIRECTORY_SEPARATOR` when
  loading from the file system.
* ���ļ�ϵͳ�м���Դ�ļ�ʱ�������ռ��еķָ�������ת��Ϊ `DIRECTORY_SEPARATOR`��

* Each `_` character in the CLASS NAME is converted to a
  `DIRECTORY_SEPARATOR`. The `_` character has no special meaning in the
  namespace.
* �����е�ÿ�� `_` ������ת��Ϊһ�� `DIRECTORY_SEPARATOR`��`_` �ڿռ�����û��ʲô��������塣

* The fully-qualified namespace and class is suffixed with `.php` when
  loading from the file system.
* ��ȫ��׼�������ռ������ļ�ϵͳ����Դ�ļ�ʱ������� `.php` ��׺��

* Alphabetic characters in vendor names, namespaces, and class names may
  be of any combination of lower case and upper case.
* ��֯�����ռ������������ɴ�Сд��ĸ��϶��ɡ�

Examples
--------

ʾ��
--------

* `\Doctrine\Common\IsolatedClassLoader` => `/path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`
* `\Symfony\Core\Request` => `/path/to/project/lib/vendor/Symfony/Core/Request.php`
* `\Zend\Acl` => `/path/to/project/lib/vendor/Zend/Acl.php`
* `\Zend\Mail\Message` => `/path/to/project/lib/vendor/Zend/Mail/Message.php`

Underscores in Namespaces and Class Names
-----------------------------------------

�ռ����������е��»���
-----------------------------------------

* `\namespace\package\Class_Name` => `/path/to/project/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/path/to/project/lib/vendor/namespace/package_name/Class/Name.php`

The standards we set here should be the lowest common denominator for
painless autoloader interoperability. You can test that you are
following these standards by utilizing this sample SplClassLoader
implementation which is able to load PHP 5.3 classes.

����������Ϊʵ��ͨ�õ��Զ����ض��ƶ�����ͱ�׼��
����������ܹ��Զ�����PHP 5.3���SplClassLoader��������Ĵ����Ƿ������Щ��׼��

Example Implementation
----------------------

ʵ��
----------------------

Below is an example function to simply demonstrate how the above
proposed standards are autoloaded.

������һ����������������׼��ʵ���Զ����ص�ʾ��������

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

SplClassLoader Implementation
-----------------------------

SplClassLoader ʵ��
-----------------------------

The following gist is a sample SplClassLoader implementation that can
load your classes if you follow the autoloader interoperability
standards proposed above. It is the current recommended way to load PHP
5.3 classes that follow these standards.

�����gist��һ���������潨��ı�׼���Զ��������SplClassLoaderʵ����
����������Щ��׼������PHP 5.3����Ƽ�������

* [http://gist.github.com/221634](http://gist.github.com/221634)

