# 一些代码片段

#### js修改url中某个指定的参数的值

```shell
# url 目标url 
# arg 需要替换的参数名称 
# arg_val 替换后的参数的值 
# return url 参数替换后的url 
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