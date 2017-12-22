# checkbox**标签**

#### checkbox**标签的属性 :**

> checkbox标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **default\_val：** 默认选中
> >
> > **readonly：** 是否可选
> >
> > \***sql\_key：** SQL语句对应的key , 比如：select city\_id,city\_name from bs\_city where city\_type='4' and city\_id not in \('331081002000','331081103000'\) 
> >
> > \***show\_field：** 显示名对应的字段
> >
> > \***value\_field：** 值对应的字段
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",checkbox标签的默认size为12

#### checkbox标签的引入方式 :

```
<@checkbox id="bs_city2" name="bs_city2_name" default_val="331081004000,331081105000,331081107000,331081110000" readonly="true" sql_key="bs_city2" show_field="city_name" value_field="city_id" size="12" />
```

#### checkbox标签显示效果图 :

![](/assets/checkbox.png)

