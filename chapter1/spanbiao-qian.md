# span**标签**

#### span**标签的属性 :**

> span标签有7个属性分别为为id、name、class、size、label、value、translate_code_type
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **class ：** class属性
>>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为1
> >
> > **label :** label为select标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **value：** value属性，用于存放显示值
>>
> > **translate\_code\_type：** translate\_code\_type属性，值为该span值在sys_code表的转义类型，如：
>>
>>translate\_code\_type="STATE"






#### span标签的引入方式 :

```
   <@span>属性显示</@span>
    
   <@span class="text-warning" value="属性显示1"/>

   <@span class="text-error" value="属性显示2"/>

   <@span class="text-info" value="属性显示3"/>

   <@span class="text-success" value="属性显示4"/>
```
#### span标签的显示结果 :

![](/assets/span.png)

