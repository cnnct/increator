# 子tab**标签组**

#### 子tab标签组：

> > 子tab标签组包含两个标签，分别为child\_tab（子tab标签最外层）、child\_tab\_content（子tab标签内容包裹层）

#### child\_tab**标签的属性 :**

> child\_tab标签有4个属性分别为为id、name、size、title；
>
> **其中title为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",child\_tab标签的默认size为12
> >
> > title**\* :** title属性是child\_tab标签记录下一级的信息的属性；
> >
> > 如child\_info="child;sysfunc3;TITLE;FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值**

#### child\_tab\_content**标签的属性 :**

> cas\_select\_child标签有5个属性分别为为id、name、size、label、child\_info；
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > **id \* ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",cas\_select\_child标签的默认size为5
> >
> > **label : **label为cas\_select\_child标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **child\_info  :** child\_info属性是cas\_select\_child标签记录下一级的信息的属性；
> >
> > 如child\_info="child;sysfunc3;TITLE;FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值，但是如果该级为最后一级则child\_info属性不必存在**



