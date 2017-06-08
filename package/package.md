# 项目里会用到的库

### 1.日期处理 [moment](http://momentjs.cn/)

#### 安装

```shell
  bower install moment --save # bower
  npm install moment --save   # npm
  Install-Package Moment.js   # NuGet
  spm install moment --save   # spm
  meteor add momentjs:moment  # meteor
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

