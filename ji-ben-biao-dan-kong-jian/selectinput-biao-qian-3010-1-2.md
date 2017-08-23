# select_input**标签**

#### select_input**标签的属性 :**

> select_input标签有8个属性分别为为id、name、size、type、label、value、readonly,select_item
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为5
> >
> > **type ：** type属性，默认为“text”
> >
> > **label ：** label为input标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
> >
> > **value  ：** value属性
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
>>  **select\_item ：**select的option选项


#### select_input标签的引入方式 :

```
    <@select_input label="邮编:,true,2" id="name" name="name"   size="4"  select_item="栏目1,栏目2"/>

   
```

#### select_input标签的显示结果:



