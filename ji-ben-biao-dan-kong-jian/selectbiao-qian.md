# Select**标签**

#### select**标签的属性 :**

> select标签属性分别如下：
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为5
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **label :** label为select标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
> >
> > **select\_more :** select\_more为是否多选,可以填的数值为"true","false",默认为false，和choice\_have、
> >
> > search\_have属性配合使用
> >
> > **choice\_have ：** choice\_have为是否需要第一项加入“--请选择--”这一项,可以填写的数值为"true","false",
> >
> > 默认值为false,如果select\_more属性为true时,choice\_have必须为false,
> >
> > 因为当select标签为多选标签时，默认加入了“--请选择--”项
> >
> > **search\_have :** search\_have为是否需要搜索框，该属性在select\_more属性为true时可用，可以填写的值
> >
> > 为"true","false",默认false，在【1.2.3】版本后，不需要select\_more属性配合为true时也可以使用
> >
> > ** sql\_key  :** sql\_key属性为select标签后台执行的sql的key值，sql可以是完整的，也可以是拥有“？”占位符的sql，配合sql\_condition属性使用；
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > ** value\_field  :** value\_field属性是指select标签选项option的value值是由表中哪个字段来赋值；
> >
> > ** show\_field  :** show\_field属性是指select标签选项option的text值是用表中哪个字段来赋值；
> >
> > **default\_val :** default\_val属性是指select标签的默认选中值，该值为option的value值，当select\_more 属性为“true”时，可以多选，
> >
> > 如default\_val="0,2",注意分隔符；
> >
> > **cust_get_data_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为Map类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >


#### select标签的引入方式 :

```
<@select sql_key="syscode2"   id="sdf" sql_condition="ACC_RECHG_TYPE" name="name" show_field="CODE_NAME" value_field="CODE_VALUE" default_val="2" choice_have="true" size="6"/>

<@select sql_key="syscode1" name="name" id="hjdf" show_field="CODE_NAME" value_field="CODE_VALUE" default_val="1,2"   size="6" select_more="true" search_have="true"/>
```

#### 对应sql语句 :

![](/assets/select_sql.png)

#### 显示结果:

![](/assets/select1.png)![](/assets/select2.png)

