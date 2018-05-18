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
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸, 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；  
label="name" ；label="name,,2" 即三个值都非必填项，【2.5】版本后在view_para文件里的must_star_position属性可以控制must_star的加载左右位置，默认left
> >
> > **default\_val：** 默认选中
> >
> > **readonly：** 是否可选
> >
> > **sql\_key：** SQL语句对应的key , 比如：select city\_id,city\_name from bs\_city where city\_type='4'
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > \***show\_field：** 显示名对应的字段
> >
> > \***value\_field：** 值对应的字段
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",radio标签的默认size为12
> >
> > **cust_get_data_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为Map类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **body_size【2.4】 ：** body_size为尺寸属性，用于控制大小，可填值small和large,默认small
> >


#### radio标签的引入方式 :

```
<@radio id="bs_city1" name="bs_city1_name" default_val="331081100000" readonly="true" sql_key="bs_city1" show_field="city_name" value_field="city_id" size="12" />
```

#### radio标签显示效果图 :

![](/assets/radio.png)

