# span**标签**

#### span**标签的属性 :**

> span标签有5个属性分别为为id、name、class、size、label
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **class ：** class属性
>>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为5
> >
> > **label :** label为select标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >

#### span标签的引入方式 :

```
   <@span>属性显示</@span>
    
   <@span class="text-warning">属性显示1</@span>

   <@span class="text-error">属性显示2</@span>

   <@span class="text-info">属性显示3</@span>

   <@span class="text-success">属性显示4</@span>
```
#### span标签的显示结果 :

![](/assets/span.png)

