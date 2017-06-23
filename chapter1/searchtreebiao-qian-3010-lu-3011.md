# search\_tree**标签**

#### search\_tree**标签的属性 :**

> search\_tree标签有8个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > \***tree\_id：** 树的id
> >
> > **checkbox\_have：** 是否为复选框,默认单选
> >
> > \***sql\_key：** SQL语句对应的key
> >
> > **label：** label标签
> >
> > **sql\_condition：** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE;session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",search\_tree标签的默认size为5

#### search\_tree标签的引入方式 :

```
<@search_tree id="search" name="search_name" tree_id="search_tree" sql_key="sysfunc7" checkbox_have="true" size="6" />
```

#### search\_tree标签显示效果图 :

![](/assets/search_tree.png)



