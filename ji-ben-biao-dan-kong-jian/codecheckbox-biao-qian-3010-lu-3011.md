# code\_checkbox**标签**

#### code\_checkbox**标签的属性 :**

> code\_checkbox标签有8个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **label：** label为select标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> >label="name" ；label="name,,2" 即三个值都非必填项
> >
> > \***code\_type：** 从Sys\_Code表查询的字段
> >
> > **default\_val：** 默认选中
> >
> > **readonly：** 是否可选
> >
> > **no\_show：** 过滤的选项
> >
> > **only\_show：** 只显示的选项
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",code\_checkbox标签的默认size为12
> > **switch_style【2.4】：** 该属性用于控制switch风格样式，现有六种样式，如switch_style="1",可填值1到6，默认无switch样式
> >


#### code\_checkbox标签的引入方式 :

```
<@code_checkbox id="code_type2" name="code_type2_name" code_type="ORDER_STATE" default_val="09,28,58" readonly="true" no_show="19,71" only_show="09,28,58,18,41,71" size="12" />
```

#### code\_checkbox标签显示效果图 :

![](/assets/code_checkbox.png)

