# function openNewMenuTab\(options\)方法

js方法addTabs\(options\)由于用在首页，所以之前子页面调用时比较麻烦，且传参到后台很麻烦，所以封装了一个openNewMenuTab方法，在init\_page加载过的页面都可直接调用。

调用方式：

openNewMenuTab\(options\);

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
    page_refresh: true,
    para:{para1:'123',para2:'abc'}
}
openNewMenuTab(options);
```

注：由于对url进行了编码处理，所以后台需要对url中包含的参数进行解码，如下所示：

```
funcId = URLDecoder.decode(funcId, "utf-8");
```

# function openNewMenuTabSimple\(funcId,para,refresh\)

对openNewMenuTab的简化版本，可直传入funcid，即可。【2.8】中新增

