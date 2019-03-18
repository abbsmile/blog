---
title: 'thinkcmf:cmf_password()及其它'
date: 2017-03-19 23:52:24
categories:
- ThinkCMF
tags:
- ThinkCMF
---

![th.jpeg](https://upload-images.jianshu.io/upload_images/2875232-7eb16786a7da57f5.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

笔者让阿里云上数据库覆盖了本地数据库，然后发现，云端可登录的帐号密码在本地登陆不了。

查看cmf源码，定位cmf_password()函数，发现它使用了数据库配置文件中的一个参数。而数据库配置文件，由于做了特殊设置git时本地与云端不同步。

换句话：也就是云端加密与本地加密的盐不同。
```
/**
 * CMF密码加密方法
 * @param string $pw 要加密的原始密码
 * @param string $authCode 加密字符串
 * @return string
 */
function cmf_password($pw, $authCode = '')
{
    if (empty($authCode)) {
        $authCode = Config::get('database.authcode');
    }
    $result = "###" . md5(md5($authCode . $pw));
    return $result;
}
```

虽然是个小问题，但进一步有进一步的乐趣。发现了问题还是要找本质原因，虽然有时可以通过迂回的方法解决，但习惯了这样总是不好的。

