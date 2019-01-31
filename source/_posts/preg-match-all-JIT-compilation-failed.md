---
title: 'preg_match_all(): JIT compilation failed'
date: 2018-12-20 10:54:49
catagories: Mac Composer
tags: Composer
---

在这个电脑上装个laravel,结果composer出现了问题，糟心……查了下原因，php7.3的bug:

```
composer create-project laravel/laravel laravel54 "5.4.*"
```
```
PHP Warning:  preg_match_all(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 137

Warning: preg_match_all(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 137

PHP Warning:  preg_match(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 762

Warning: preg_match(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 762
PHP Warning:  preg_match(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 766

Warning: preg_match(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 766
PHP Warning:  preg_split(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 661

Warning: preg_split(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Application.php on line 661
PHP Warning:  preg_replace(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 36

Warning: preg_replace(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 36

  [ErrorException]
  preg_match(): JIT compilation failed: no more memory


PHP Warning:  preg_match_all(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 199

Warning: preg_match_all(): JIT compilation failed: no more memory in phar:///usr/local/bin/composer/vendor/symfony/console/Formatter/OutputFormatter.php on line 199
create-project [-s|--stability STABILITY] [--prefer-source] [--prefer-dist] [--repository REPOSITORY] [--repository-url REPOSITORY-URL] [--dev] [--no-dev] [--no-custom-installers] [--no-scripts] [--no-progress] [--no-secure-http] [--keep-vcs] [--remove-vcs] [--no-install] [--ignore-platform-reqs] [--] [<package>] [<directory>] [<version>]
```

解决方法：
```
This is a known PHP 7.3 bug.

As a temporary fix, edit your php.ini file (in my case: vi /usr/local/etc/php/7.3/php.ini), disable PHP PCRE JIT compilation by changing:

;pcre.jit=1
to

pcre.jit=0
```s

笔者开始还折腾了一会，，，因为装的php版本太多了，不知道以前装的composer跟哪个有关系，有时间还是要整理下。

至于为什么composer和php.ini有关系，把这个问题先放在这里？