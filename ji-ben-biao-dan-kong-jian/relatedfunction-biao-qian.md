# related\_function**标签**

#### related\_function**标签的属性 :**

> related\_function标签有10个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** func\_id
> >
> > \***title ：** 标题
> >
> > **close：** 是否可关闭
> >
> > **url：** url地址
> >
> > **parent\_id：** 父func\_id
> >
> > \***onclick：** onclick事件
> >
> > **active：** 是否激活
> >
> > **end：** 是否最后一个

#### related\_function标签的引入方式 :

```
  <@related_function id="010602" title="测试1" close="true" url="/manageplat/sys/auth/role/index" parent_id="0106" onclick="newTab(this)" active="true"/>
  <@related_function id="010603" title="测试2" close="true" url="/manageplat/sys/auth/role/index" parent_id="0106" onclick="newTab(this)" active="false"/>
  <@related_function id="010606" title="测试3" close="true" url="/manageplat/sys/auth/role/index" parent_id="0106" onclick="newTab(this)" active="true"/>
  <@related_function id="010602" title="测试4" close="true" url="/manageplat/sys/auth/role/index" parent_id="0106" onclick="newTab(this)" active="false"/>
  <@related_function id="010603" title="测试5" close="true" url="/manageplat/sys/auth/role/index" parent_id="0106" onclick="newTab(this)" active="true" end="true"/>
```

然后再写一个对应的onclick方法：

```
function newTab(obj){
    // 例如，打开一个新tab页：
    parent.addTabs({id:obj.id,title: obj.title,close: obj.close,url:obj.url,parent_id: obj.parentId});
}
```

#### related\_function标签显示效果图 :

![](/assets/related_function.png)

