## wap总结

1. meta标签 [<head>标签中到底可以放什么?](https://github.com/xlslucky/HEAD)

2. css

去除系统默认appearance的样式,常用于IOS下移除原生样式

```shell
-webkit-appearance: none;
```

消除在移动浏览器上触发click事件与一个物理Tap(敲击)之间的300延迟。

```js
// Android 设备上的 google浏览器 （Chrome） 32+ 版本，在meta头信息中设置 width=device-width 没有300毫秒的延时，所以也无需使用本插件。
<meta name="viewport" content="width=device-width, initial-scale=1">

// 使用fastclick
https://github.com/ftlabs/fastclick/blob/master/lib/fastclick.js
if ('addEventListener' in document) {
    document.addEventListener('DOMContentLoaded', function() {
        FastClick.attach(document.body);
    }, false);
}
```