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