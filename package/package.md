# 项目里会用到的库

### 1.日期处理 [moment](http://momentjs.cn/)

#### 安装

```shell
  npm install moment --save   # npm
```

#### 日期格式化

```shell
  moment().format('MMMM Do YYYY, h:mm:ss a'); // 六月 8日 2017, 3:36:41 下午
  moment().format('dddd');                    // 星期四
  moment().format("MMM Do YY");               // 6月 8日 17
  moment().format('YYYY [escaped] YYYY');     // 2017 escaped 2017
  moment().format();                          // 2017-06-08T15:36:41+08:00
```

#### 相对时间

```shell
  moment("20111031", "YYYYMMDD").fromNow(); // 6 年前
  moment("20120620", "YYYYMMDD").fromNow(); // 5 年前
  moment().startOf('day').fromNow();        // 16 小时前
  moment().endOf('day').fromNow();          // 8 小时内
  moment().startOf('hour').fromNow();       // 38 分钟前
```

### 2.实用工具 [utility](https://github.com/node-modules/utility)

#### 安装

```shell
  npm install utility --save   # npm
```
* md5
* sha1
* sha256
* hmac
* decode and encode
* Date utils
* Number utils
* Timers
* map
* String utils
* Try
* argumentsToArray
* JSON
* Object.assign
* benchmark

### 3.nodejs实现promise [Q](https://github.com/kriskowal/q)

> promise是解决JS中回调层次太深 代码难懂 改起来麻烦的问题。

> Q是nodeJs中实现promise的包之一，是nodeJs中比较常用的一个库。

#### 安装

```shell
  npm install q --save   # npm
```

```shell
  #例
  var request = require('request');
  var Q = require('q');
  function fetch (url) {
    var defer = Q.defer();
    request(url, function (error, body) {
      if (error) {
        defer.reject(error)
      }else {
        var resp = body.body;
        if (typeof resp === 'string') {
          try {
            resp = JSON.parse(resp);
            defer.resolve(resp);
          } catch(e) {
            defer.resolve({});
          }
        }else {
          defer.resolve(resp)
        }
      }
    })
    return defer.promise;
  }
```

### 解析url [query-string](https://github.com/sindresorhus/query-string)

#### 安装

```shell
    npm install query-string --save   # npm
```

```js
  var qs = require('query-string');

  var search = '?id=10086&name=xu';
  console.log(qs.parse(search))
  // => { id: '10086', name: 'xu' }

  var hash = '#num=10';
  console.log(qs.parse(hash))
  // => { num: '10' }

  console.log(qs.stringify({size: 10, sum: 212}))
  // => size=10&sum=212
```
