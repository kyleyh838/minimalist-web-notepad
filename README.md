# Minimalist Web Notepad

This is an open source clone of notepad.cc, which is now defunct.

See demo at https://notes.orga.cat or https://notes.orga.cat/whatever.

我用的是宝塔面板，首先安装 nginx 和 php （我用的 nginx 1.21+php 7.4）

1.打开
https://github.com/pereorga/minimalist-web-notepad
点击绿色的“Code”，点击“Download ZIP”下载，得到文件“minimalist-web-notepad-master.zip”

2.在宝塔新建一个网站，在“网站配置”中加入以下字段并保存（作用是启用 URL 重写）
location / {
    rewrite ^/([a-zA-Z0-9_-]+)$ /index.php?note=$1;
}

3.上传“minimalist-web-notepad-master.zip”并解压到网站根目录

4.编辑解压出来的“index.php”文件，修改第四行中的网址为自己的网址

5.结束。其实上述内容基本都写在了项目页面...

------------------------------------
这个记事本，感觉挺好用的，在域名后面加上随机字符就可以“生成一个新的记事本”。
例如域名是1.com
输入 1.com/123 是一个记事本
输入 1.com/fsdfa 也是一个记事本

我个人使用这个的场景在于存到快捷书签栏，需要记录的时候点一下打开然后记录进去，其他设备输入域名+相同的后缀就能看到记录的内容。

## Installation

At the top of `index.php` file, change `$base_url` variable to point to your
site.

Make sure the web server is allowed to write to the `_tmp` directory.

### On Apache

You may need to enable mod_rewrite and set up `.htaccess` files in your site configuration.
See [How To Set Up mod_rewrite for Apache](https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04).

### On Nginx

To enable URL rewriting, put something like this in your configuration file:

If the project resides in the root directory:
```
location / {
    rewrite ^/([a-zA-Z0-9_-]+)$ /index.php?note=$1;
}
```

If the project resides in a subdirectory:
```
location ~* ^/notes/([a-zA-Z0-9_-]+)$ {
    try_files $uri /notes/index.php?note=$1;
}
```

## Branches

To install it with Docker see the [docker](https://github.com/pereorga/minimalist-web-notepad/tree/docker) branch.

A version that allows for encryption using the Web Crypto API is available at the [encryption](https://github.com/pereorga/minimalist-web-notepad/tree/encryption) branch.


## Copyright and license

Copyright 2012 Pere Orga <pere@orga.cat>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this work except in compliance with the License.
You may obtain a copy of the License at:

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
