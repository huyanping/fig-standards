# Autoloader

# �Զ�������

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

[RFC 2119](http://tools.ietf.org/html/rfc2119) �еı���(MUST)������(MUST NOT)��
����(SHOULD)��������(SHOULD NOT)������/����(MAY)�ȹؼ���
���ڱ���������һЩ�����Ե�������

## 1. Overview

## 1. ����

This PSR describes a specification for [autoloading][] classes from file
paths. It is fully interoperable, and can be used in addition to any other
autoloading specification, including [PSR-0][]. This PSR also describes where
to place files that will be autoloaded according to the specification.

��� PSR ��������ͨ���ļ�·�� [autoloading][] ���ָ�ϡ�
������ȫ�ɻ������ģ����Զ���ʹ���������Զ�����淶��
 ���� [PSR-0][] ����� PSR ����������ι淶����ļ����Զ����롣

## 2. Specification

## 2. ˵��

* The term "class" refers to classes, interfaces, traits, and other similar
   structures.

* "��" ��һ�����ƣ��������࣬�ṹ��traits �Լ��������ƵĽṹ��

* A fully qualified class name has the following form:

  ����������Ӧ���������·�����

      \<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>

    * The fully qualified class name MUST have a top-level namespace name,
      also known as a "vendor namespace".

    * һ������������������һ�����������ռ䣬Ҳ����������֪�� "vendor namespace"��

    * The fully qualified class name MAY have one or more sub-namespace
      names.

    * һ��������������������һ�������������ռ䡣

    * The fully qualified class name MUST have a terminating class name.

    * һ��������������������һ����ֹ������

    * Underscores have no special meaning in any portion of the fully
      qualified class name.

    * �»����������������κβ�����û���������塣
    ������ע������������PSR-0������ͬ��

    * Alphabetic characters in the fully qualified class name MAY be any
      combination of lower case and upper case.

    * һ�������������ɴ�Сд��ĸ��ɡ�

    * All class names MUST be referenced in a case-sensitive fashion.

    * ���е��������������ִ�Сд�ķ�ʽ����

* When loading a file that corresponds to a fully qualified class name ...

* ������һ���ļ���Ӧһ������������

    * A contiguous series of one or more leading namespace and sub-namespace
      names, not including the leading namespace separator, in the fully
      qualified class name (a "namespace prefix") corresponds to at least one
      "base directory".

    * һ��������һ�������������ռ���������ռ����ƣ�
      �������������ռ�ָ����� ��������������һ���������ռ�ǰ׺���������Ӧ������һ��������Ŀ¼����
      ������ע�������淭��ģ�����������ʱ�һ�û����⣩

    * The contiguous sub-namespace names after the "namespace prefix"
      correspond to a subdirectory within a "base directory", in which the
      namespace separators represent directory separators. The subdirectory
      name MUST match the case of the sub-namespace names.

    * �ڡ������ռ�ǰ׺����������������ռ����ƶ�Ӧ����Ŀ¼�еġ�����Ŀ¼����
      ���е������ռ�ָ�����ʾĿ¼�ָ�����
      ��Ŀ¼���Ʊ���ƥ���������ռ����ơ�

    * The terminating class name corresponds to a file name ending in `.php`.
      The file name MUST match the case of the terminating class name.

    * ��������Ӧ�ú� `.php` �ļ���ƥ�䡣�ļ����Ĵ�Сд����ƥ�䣻

* Autoloader implementations MUST NOT throw exceptions, MUST NOT raise errors
of any level, and SHOULD NOT return a value.

* �Զ���������ʵ�ֲ����׳��κ��쳣�������׳��κεȼ��Ĵ���Ҳ���ܷ���ֵ��


## 3. Examples

## 3. ʾ��

The table below shows the corresponding file path for a given fully qualified
class name, namespace prefix, and base directory.

���±��չʾ������������������������ļ�·���Ĺ�ϵ��

| Fully Qualified Class Name    | Namespace Prefix   | Base Directory           | Resulting File Path
| ----------------------------- |--------------------|--------------------------|-------------------------------------------
| ����������                    | �����ռ�ǰ׺       | ����Ŀ¼                 | ʵ�ʵ����ļ�·��
| \Acme\Log\Writer\File_Writer  | Acme\Log\Writer    | ./acme-log-writer/lib/   | ./acme-log-writer/lib/File_Writer.php
| \Aura\Web\Response\Status     | Aura\Web           | /path/to/aura-web/src/   | /path/to/aura-web/src/Response/Status.php
| \Symfony\Core\Request         | Symfony\Core       | ./vendor/Symfony/Core/   | ./vendor/Symfony/Core/Request.php
| \Zend\Acl                     | Zend               | /usr/includes/Zend/      | /usr/includes/Zend/Acl.php

For example implementations of autoloaders conforming to the specification,
please see the [examples file][]. Example implementations MUST NOT be regarded
as part of the specification and MAY change at any time.

�����е��Զ��������ǳ���Ӧ���ָ�ϣ������ [examples file][] ��������������Ϊָ�ϵ�һ���֣�������ʱ���ı䣻

[autoloading]: http://php.net/autoload
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[examples file]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader-examples.md
