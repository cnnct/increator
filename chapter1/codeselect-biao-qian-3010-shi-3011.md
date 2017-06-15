# code\_select**标签**

#### code\_select**标签的属性 :**

> code\_select标签有12个属性分别为为id、name、size、readonly、label、select\_more、choice\_have、
>
> search\_have、default\_val、no\_show、only\_show、code\_type；**其中id、code\_type为必填项,下面必填项加上了\*号**；
>
> > **id \*** **：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为5
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **label : **label为select标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **select\_more : **select\_more为是否多选,可以填的数值为"true","false",默认为false，和choice\_have、
> >
> > search\_have属性配合使用
> >
> > **choice\_have :** choice\_have为是否需要第一项加入“--请选择--”这一项,可以填写的数值为"true","false",
> >
> > 默认值为false,如果select\_more属性为true时,choice\_have必须为false,
> >
> > 因为当select标签为多选标签时，默认加入了“--请选择--”项
> >
> > **search\_have :** search\_have为是否需要搜索框，该属性在select\_more属性为true时可用，可以填写的值
> >
> > 为"true","false",默认false
> >
> > **show\_field \* :** show\_field属性是指select标签选项option的text值是用表中哪个字段来赋值；
> >
> > **default\_val :** default\_val属性是指select标签的默认选中值，下标从0开始，单select\_more 属性为“true”时，可以多选，
> >
> > 如default\_val="0;2",注意分隔符；
> >
> > **no\_show ：**不显示的option项，下标从0开始，和only\_show属性不能同时使用，如果同时使用，则两属性失效
> >
> > **only\_show ：**只显示的option项，下标从0开始，和no\_show属性不能同时使用，如果同时使用，则两属性失效
> >
> > **code\_type \* : ** 指定查询sys\_code表中code\_type表字段的值作为数据加载时使用

#### code\_select标签的引入方式 :

```
<@code_select id="select-1" id="dsf" name="name" code_type="AREA_TYPE" default_val="1"  no_show="1"  size="6" choice_have="true" select_more="" />    

<@code_select id="select-2" id="sdfs" name="name" code_type="AREA_TYPE" default_val="0;1"   size="6"  select_more="true" search_have="true"/>
```

![](/assets/code_select1.png)![](/assets/code_select2.png)

