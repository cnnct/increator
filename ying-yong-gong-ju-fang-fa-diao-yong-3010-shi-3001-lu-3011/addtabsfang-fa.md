# addTabs方法

js方法addTabs\(options\)由于用在首页，所以之前子页面调用时比较麻烦，且传参到后台很麻烦，所以封装了一个addTabs方法，在init\_page加载过的页面都可直接调用。

调用方式：

addTabs\(options\);

options为json对象，属性有：

id

title

close

url

parent\_id

para

调用示例：

```
var options = {
    id:'010602',
    title: '部门管理',
    close: true,
    url: '/manageplat/sys/auth/brch/index',
    parent_id: '0106',
    para:{para1:'123',para2:'abc'}
}
addTabs(options);
```



