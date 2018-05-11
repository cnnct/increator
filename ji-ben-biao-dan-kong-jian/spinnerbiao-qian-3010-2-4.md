# spinner**标签**

#### spinner**标签的属性 :**

> spinner标签属性分别为如下：
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为4
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
> > **body_size：** 控制大小尺寸，可填值small和large，默认small
> >
> > **data_min：** 为最小值属性，默认0
> >
> > **data_max：** 为最大值属性，默认100
> >
> > **data_step：** 为步长属性，默认1
> >


#### spinner标签的引入方式 :

```
    <@input label="邮编:,true,2" id="name" name="name"  type="text" size="4"  />

    <@input label="邮件:,true,2" id="email" name="email"  type="email" size="4" />
```

#### spinner标签的显示结果:

![](/assets/input.png)

