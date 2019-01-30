---
title: Laravel5.4数据库迁移及几个问题
date: 2019-01-30 14:55:35
categories: Laravel
tags: Laravel migration command mysql php
---

## 场景

不同于Yii2,ThinkPHP和其它原生PHPCMS，Laravel框架利用migration将数据库表结构的操作交由代码控制，确实省心省力。相比于python的flask,笔者更喜欢Laravel的设计。

1. 数据库表结构的操作，虽由代码控制，但并没有和逻辑代码混淆在一起；
2. 类似于git和svn,版本迭代功能，虽不怎么完美，但倒也不失为还不错的多人合作解决方案（目前公司多人合作方案是共用一个远程数据库，这样注重了结果，但没有记录修改数据库的过程）
3. 目前笔者所知的数据库设计方式有三种：CodeFirst,ModelFirst,databaseFirst

- databaseFirst
    到目前为止，笔者用的最多的还是databaseFirst。利用navicat或者commandLine根据需求直接建表。这种方式比较中性。
    
- ModelFirst
    利用建模工具创建数据库，笔者还没有做过。不过相信dba利用这些工具建表时，所考虑的代码层面肯定很少很少。
    
- CodeFirst
    如果想兼顾到代码，相信CodeFirst是最好的方式。作为一个程序员(笔者不喜欢给自己贴标签,只能说当前在公司还是靠程序员这个职位养活自己),或者说暂时还是程序员，不是运维也不是dba,用CodeFist方式操作数据库，更能兼顾到业务逻辑代码和数据库的一体性。
    
## 过程

刚安装Laravel54后，遇到两个小bug.

> 提示User表已存在 

```
 /Applications/MAMP/htdocs/laravel54  ./artisan migrate

In Connection.php line 647:

  SQLSTATE[42S01]: Base table or view already exists: 1050 Table 'users' already exists (SQL: create table `users` (`id` int unsigned not null auto_increment primary key, `name` varchar(191) not
   null, `email` varchar(191) not null, `password` varchar(191) not null, `remember_token` varchar(100) null, `created_at` timestamp null, `updated_at` timestamp null) default character set utf8
  mb4 collate utf8mb4_unicode_ci)


In Connection.php line 449:

  SQLSTATE[42S01]: Base table or view already exists: 1050 Table 'users' already exists
```

笔者查看user表相关逻辑，有了那么一句：
```
  /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('users');
    }
```
有毒，本想直接操作Navicate的，后来想想算了，直接命令行吧,下面一段直接stackoverflow抄的，有效：
```
php artisan tinker

Then

Schema::drop('books')

(and exit with q)

Now, you can successfully php artisan migrate:rollback and php artisan migrate.
```

发现删完再migration的时候不会出毛病了……好吧！！！

> 字节长度造成的bug

```
 /Applications/MAMP/htdocs/laravel54  ./artisan migrate

In Connection.php line 647:

  SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes (SQL: alter table `users` add unique `users_email_unique`(`email`))


In Connection.php line 449:

  SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes
```

查了下user表的email,string类型。Laravel 5.4 把默认数据库字符集更改成 utf8mb4，如果运行的是 MySQL v5.7.7 及更高版本，那么就不会出现本文提到的错误。

因为utf8mb4中是4个byte对应一个字符。767/4 = 191

```
namespace App\Providers;

use Illuminate\Support\Facades\Schema;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        Schema::defaultStringLength(191);
    }
}
```

## 结论

1. migration是个好东西，常用migration命令可以在命令行中查，这里不罗列了；
2. codeFirst这种思想不错；
3. mysql5.6和更高版本的不同确是要引起足够重视。

