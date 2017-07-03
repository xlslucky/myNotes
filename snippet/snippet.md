# 一些代码片段

#### js修改url中某个指定的参数的值

```js
// url 目标url 
// arg 需要替换的参数名称 
// arg_val 替换后的参数的值 
// return url 参数替换后的url 
function changeURLArg(url,arg,arg_val){ 
  var pattern=arg+'=([^&]*)'; 
  var replaceText=arg+'='+arg_val; 
  if(url.match(pattern)){ 
    var tmp='/('+ arg+'=)([^&]*)/gi'; 
    tmp=url.replace(eval(tmp),replaceText); 
    return tmp; 
  }else{ 
    if(url.match('[\?]')){ 
      return url+'&'+replaceText; 
    }else{ 
      return url+'?'+replaceText; 
    } 
  } 
  return url+'\n'+arg+'\n'+arg_val; 
} 
```

#### js解析地址栏

```js
// name 地址栏参数名
function getQueryString (name) {
  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");
  var r = window.location.search.substr(1).match(reg);
  if (r != null) return decodeURIComponent(r[2]);
  return "";
}
```

#### js设置、获取、删除cookies

```js
// 设置cookies
// setCookie('name', 'xlslucky')
function setCookie(name,value) { 
  var Days = 30; 
  var exp = new Date(); 
  exp.setTime(exp.getTime() + Days*24*60*60*1000); 
  document.cookie = name + "="+ escape (value) + ";expires=" + exp.toGMTString(); 
}

// 获取cookies
// getCookie('name')
function getCookie(name) { 
  var arr,reg=new RegExp("(^| )"+name+"=([^;]*)(;|$)");
  if(arr=document.cookie.match(reg)) return unescape(arr[2]); 
  else return null; 
}

// 删除cookies
// delCookie('name')
function delCookie(name) { 
  var exp = new Date(); 
  exp.setTime(exp.getTime() - 1); 
  var cval=getCookie(name); 
  if(cval!=null) document.cookie= name + "="+cval+";expires="+exp.toGMTString(); 
} 
```

```js
// 页面标签切换 改变title
(function() {
    var OriginTitile = document.title, titleTime;
    document.addEventListener('visibilitychange', function() {
        if (document.hidden) {
            document.title = '死鬼去哪里了！';
            clearTimeout(titleTime);
        } else {
            document.title = '(つェ⊂)咦!又好了!';
            titleTime = setTimeout(function() {
                document.title = OriginTitile;
            },2000);
        }
    });
})();
```