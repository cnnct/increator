# span**标签**

#### span**标签的属性 :**

> span标签有7个属性分别为为id、name、class、size、label、value、translate\_code\_type
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **class ：** class属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为4
> >
> > **label :** label为select标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项，【2.5】版本后在view_para文件里的must_star_position属性可以控制must_star的加载左右位置，默认left
> >
> > **value：** value属性，用于存放显示值
> >
> > **translate\_code\_type：** translate\_code\_type属性，值为该span值在sys\_code表的转义类型，如：
> >
> > translate\_code\_type="STATE"
>>
> > **color【2.4】：** color属性，用于控制颜色，可填值success,info,warning,danger,primary
> >
> > **body_size【2.4】：** body_size属性，用于控制尺寸大小，可填值small，middle,large,默认small
> >
> > **font_strong【2.4】：** font_strong属性，用于控制是否加粗，可填值true，false，默认false
> >



#### span标签的引入方式 :

```
   <@span>属性显示</@span>

   <@span class="text-warning" value="属性显示1"/>

   <@span class="text-error" value="属性显示2"/>

   <@span class="text-info" value="属性显示3"/>

   <@span class="text-success" value="属性显示4"/>
   
   <@span class="text-danger" value="属性显示5"/>红色
```

#### span标签的显示结果 :

![](/assets/span.png)

