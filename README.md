Share.js
===

> 🚨 此项目已经年久失修，其实分享就是一个个链接而已，每个链接里传递一些内容，所以定制需求比较高的话建议自己实现，没啥难度。

一键分享到微博、QQ好友、微信、Twitter等社交网站。

![image](https://user-images.githubusercontent.com/55282569/202605758-5d29e048-ecd5-4951-a633-cff83da6400d.png)

图标来自fontawesome

# 安装使用

1. 使用CDN引入
```html
<div class="blog-share" style="margin-bottom: 1.5rem;"></div>
<link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.2.0/css/all.min.css" />
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/yaleiyale/share.js@1.0/dist/share.min.css">
<script src="https://cdn.jsdelivr.net/gh/yaleiyale/share.js@1.0/dist/share.min.js"></script>
<script>
    const config = {
        disabled: ['weixin'],
    };
    socialShare('.blog-share', config);
</script>
```
当你使用类名为 `social-share` 时不需要手动初始化

2. 手动下载或者 git clone 本项目。

## 自定义配置

所有配置**可选**， 通常默认就满足需求：

可用的配置有：

```js

url                 : '', // 网址，默认使用 window.location.href
source              : '', // 来源, 默认读取head标签：<meta name="site" content="http://overtrue" />
title               : '', // 标题，默认读取 document.title 或者 <meta name="title" content="share.js" />
origin              : '', // 分享 @ 相关 twitter 账号
description         : '', // 描述, 默认读取head标签：<meta name="description" content="PHP弱类型的实现原理分析" />
image               : '', // 图片, 默认取网页中第一个img标签
sites               : ['qq', 'weibo','weixin',], // 启用的站点
disabled            : ['facebook', 'twitter'], // 禁用的站点
weixinQrcodeTitle   : '微信扫一扫：分享', // 微信二维码提示文字
weixinQrcodeHelper  : '<p>微信里点“发现”，扫一下</p><p>二维码便可将本文分享至朋友圈。</p>'
```

示例代码：

```js
var $config = {
    title               : '234',
    description         : '123',
    weixinQrcodeTitle   : "微信扫一扫：分享", // 微信二维码提示文字
    weixinQrcodeHelper  : '<p>微信里点“发现”，扫一下</p><p>二维码便可将本文分享至朋友圈。</p>',
};

socialShare('.social-share-cs', $config);
```

以上选项均可通过标签 `data-xxx` 来设置：

> 驼峰转为中横线，如`wexinQrcodeHelper` 的data标签为`data-wexin-qrcode-helper`

##### 禁用twitter、facebook 并设置分享的描述

```html
<div class="share-component" data-disabled="twitter,facebook" data-description="Share.js - 一键分享"></div>
```

##### 设置微信二维码标题

```html
<div class="social-share" data-weixin-qrcode-title="请打开微信扫一扫"></div>
```

##### 针对特定站点使用不同的属性（title, url, description,image...）

```html
<div class="social-share" data-weibo-title="这个标题只有的分享到微博时有用，其它标题为全局标题" data-qq-title="分享到QQ时用此标题"></div>
```

### 你也可以自定义图标

使用: `data-initialized="true"` 标签或者 `initialized` 配置项来禁用自动生成icon功能。

```html
<div class="social-share" data-initialized="true">
    <a href="#" class="social-share-fa fa-weibo"></a>
    <a href="#" class="social-share-fa fa-qq"></a>
</div>
```
以上a标题会自动加上分享链接（`a` 标签必须带 `fa-NAME` 属性，不然分享链接不会自动加上）。

### 如果你想在分享icon列表中内置一些元素，比如放一个收藏按钮在分享按钮的后面：

```html
<div class="social-share">
    <a href="javascript:;" class="social-share-fa fa-heart"></a>
</div>
```
这样并没有实现，因为结果是所有的分享按钮都创建在了收藏按钮的后面了，这时候你就可以用 `data-mode="prepend"` 来确定分享按钮创建的方式。

```html
<div class="social-share" data-mode="prepend">
    <a href="javascript:;" class="social-share-fa fa-heart"></a>
</div>
```

这样，所有的分享图标就会创建在容器的内容前面，反之可以用 `append` 创建在容器内容后面，当然这是默认的，也不需要这么做。

### 指定移动设备上显示的图标

```html
<div class="share-component" data-mobile-sites="weibo,qq"></div>
```
当在手机上打开该页面的时候就只会显示这2个图标了。

# 引用

本项目中二维码生成部分用到了开源组件：[lrsjng/jquery-qrcode](https://github.com/lrsjng/jquery-qrcode) (MIT License)

# License

 MIT


