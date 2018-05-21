# iframe自适应高度调用方法

调用方式：

iframeAutoFit(iframeObj);

options为json对象，属性有：

id：tab唯一标识

title：tab标题

close：是否有关闭按钮

url：后台地址

parent\_id：父tab唯一标识

page\_refresh\(非必填\)：tab已打开情况下，再次调用此方法，是否刷新页面

para\(非必填\)：需要传到后台的参数json对象

调用示例：

```
var options = {
    id:'010602',
    title: '部门管理',
    close: true,
    url: '/manageplat/sys/auth/brch/index',
    parent_id: '0106',
    page_refresh: 'true',
    para:{para1:'123',para2:'abc'}
}
openNewMenuTab(options);
```

注：由于对url进行了编码处理，所以后台需要对url中包含的参数进行解码，如下所示：

```
funcId = URLDecoder.decode(funcId, "utf-8");
```



