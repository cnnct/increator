# Img**标签**

#### img**标签的属性 :**

> img标签有4个属性分别为为id、size、label、src，显示原图的缩略图，点击时显示原图；
>
> **其中id、src为必填项,下面必填项加上了\*号**；
>
> > ** \*id ：** id属性
> >
> > **label :** label为select标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，
> >
> > 第一个值为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
>>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为1
> >
> > ** \*src：** src属性为指向图片指向的ftp地址
#### img标签的引入方式 :

```
   <@img label="示例图" size="6" id="testimg" src="http://192.168.153.1:8090/img.jpg"/>
```

#### img标签的显示结果 :

![](/assets/img1.png)




