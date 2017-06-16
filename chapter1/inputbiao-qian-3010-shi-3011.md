# input**标签**

#### input**标签的属性 :**

> input标签有7个属性分别为为id、name、size、type、label、value、readonly
>
> > **id ** **：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为5
> >
> > **type : **type属性，默认为“text”
> >
> > **label : **label为input标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **value  ： ** value属性
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false

#### input标签的引入方式 :

```
    <@input label="邮编;true;2" id="name" name="name"  type="text" size="4"  />

    <@input label="邮件;true;2" id="email" name="email"  type="email" size="4" />
```

![](/assets/input.png)

