# select\_list**标签**

#### select\_list**标签的属性 :**

> select\_list标签有10个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > **label：** select框label
> >
> > \***sql\_key：** SQL语句对应的key , 比如：select FILE\_ID,FILE\_ORIG\_NAME from sys\_attachment where FILE\_ID not in \(1,5\)
> >
> > \***show\_field：** 显示名对应的字段
> >
> > \***value\_field：** 值对应的字段
> >
> > **width：** 标签中select宽度，html中的px为单位
> >
> > **height：** 标签中select高度，html中的px为单位
> >
> > \***onclick：** 添加按钮onclick事件
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",search\_tree标签的默认size为4

#### select\_list标签的引入方式 :

```
<@select_list id="demoId" name="demoName" label="组员" onclick="addOption()" sql_key="bs_city2"
      show_field="file_orig_name" value_field="file_id" size="6" width="200" height="300" />
```

然后再写一个对应的onclick方法：

```
function addOption(){
  //此方法名为：select_list标签id+AddOption,传入select框option的value,text
  demoIdAddOption(1,"测试");
}
```

#### select\_list标签显示效果图 :

![](/assets/select_list.png)

