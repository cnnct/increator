# dual\_select\_list**标签**

#### dual\_select\_list**标签的属性 :**

> dual\_select\_list标签有6个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > \***sql\_key：** SQL语句对应的key
> >
> > \***show\_field：** 选项显示的名称
> >
> > \***value\_field：** 选项的值
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符
> >
> > **readonly**：是否可选
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",dual\_select\_list标签的默认size为12

#### dual\_select\_list标签的引入方式 :

```
<@dual_select_list id="dualSelectOrgName" name="dualSelectOrgName_name" show_field="org_name" value_field="org_id" sql_key="org_name2" size="8" />
```

#### dual\_select\_list标签显示效果图 :

![](/assets/dual_select_list.png)

