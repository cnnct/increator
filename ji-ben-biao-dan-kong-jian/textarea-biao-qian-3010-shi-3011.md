# Text\_area**标签**

#### text\_area**标签的属性 :**

> text\_area标签有6个属性分别为为id、name、size、readonly、label、value
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",text\_area标签的默认size为12
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **label ：** label为text\_area标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,  
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；  
> > label="name" ；label="name,,2" 即三个值都非必填项，【2.5】版本后在view\_para文件里的must\_star\_position属性可以控制must\_star的加载左右位置，默认left
> >
> > **value  ：** value属性
> >
> > **maxlength【2.8】：**最大长度属性
> >
> > **rows【2.8】：**行数，相当于高度，若不指定，默认值5

#### text\_area标签的引入方式 :

```
<@text_area label="文本域1：,false" id="username1" name="textname" value="name"  size="5" />
```

#### text\_area标签的显示结果 :

![](/assets/text_area.png)

