# iframe自适应高度调用方法

调用方式：

iframeAutoFit(iframeObj);

参数：
iframeObj:为iframe jquery对象
调用示例：

```
var iframeObj=$("#iframeId");
iframeAutoFit(iframeObj);
```

注：由于对url进行了编码处理，所以后台需要对url中包含的参数进行解码，如下所示：

```
funcId = URLDecoder.decode(funcId, "utf-8");
```



