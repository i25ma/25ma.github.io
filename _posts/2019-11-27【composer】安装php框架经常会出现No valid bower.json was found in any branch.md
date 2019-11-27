---
layout:     post
title:     【composer】安装yii2框架经常会出现No valid bower.json等错误信息
subtitle:   安装php框架经常会出现 No valid bower.json was found in any branch or tag of https://github.com/blueimp/JavaScript-Canvas-to-Blob.git, cou ld not load a package from it.
date:       2019-11-27
author:     25ma
header-img: img/post-bg-ios10.jpg
catalog: true
tags:
    - php
    - composer
    - 25ma
---


### 执行:composer install or update 时，会提示No valid bower.json was found in any branch or tag  of https://github.com/twitter/typeahead.js.git, could not load a package from it.的解决办法

- 首先执行：`composer global require "fxp/composer-asset-plugin"`，更新Composer asset plugin至最新版本
```php
Changed current directory to /root/.composer
Do not run Composer as root/super user! See https://getcomposer.org/root for details
Using version ^1.4 for fxp/composer-asset-plugin
./composer.json has been updated
Loading composer repositories with package information
Updating dependencies (including require-dev)
Package operations: 0 installs, 1 update, 0 removals
  - Updating fxp/composer-asset-plugin (`v1.4.2` => `v1.4.6`): Downloading (100%)         
Writing lock file
Generating autoload files
```

- 如果是腾讯云服务器建议使用 腾讯云的composer镜像（全量）: `https://mirrors.cloud.tencent.com/composer/`
- 这样做的好处是可以通过内网的已经缓存的源对应用进行 `install` or `update` 

- 当然，如果是非腾讯云我还是推荐使用阿里云的composer镜像（全量）：`https://mirrors.aliyun.com/composer/`

- 在执行install 或者 update 前需要确认一下： `composer.json` 配置文件中的 `repositories` 属性以及 composer 配置中指定的源是否一致，如果不一致，则修改即可

- 全局切换镜像命令： `composer config -g repos.packagist composer https://mirrors.cloud.tencent.com/composer/` 

- 接下来直接执行 install or update 就可以了

- 如果在安装过程中还遇到其他问题，欢迎在文章下方留言