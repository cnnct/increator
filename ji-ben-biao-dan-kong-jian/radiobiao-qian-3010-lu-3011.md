# radio**标签**

#### radio**标签的属性 :**

> radio标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **label ：** label为select标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，
第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号*即必填项标志；第三个值为前缀标签的尺寸,
可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
label="name" ；label="name,,2" 即三个值都非必填项
> >
> > **default\_val：** 默认选中
> >
> > **readonly：** 是否可选
> >
> > \***sql\_key：** SQL语句对应的key , 比如：select city\_id,city\_name from bs\_city where city\_type='4'
> >
> > \***show\_field：** 显示名对应的字段
> >
> > \***value\_field：** 值对应的字段
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",radio标签的默认size为12

#### radio标签的引入方式 :

```
<@radio id="bs_city1" name="bs_city1_name" default_val="331081100000" readonly="true" sql_key="bs_city1" show_field="city_name" value_field="city_id" size="12" />
```

#### radio标签显示效果图 :

![](/assets/radio.png)

