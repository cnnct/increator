# date\_time**标签**

#### button**标签的属性 :**

> button标签有8个属性分别为为id、name、size、label、size；
>
> **其中value为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为1
> >
> > **class：** class属性
> >
> > **type :** type属性，默认为“button”
> >
> > **value :** value属性主要为button显示的名字
> >
> > **icon :** icon属性为button中的图标样式，默认为“search”，可填的数值详见bootstrap官网
> >
> > **onclick :** onclick属性

#### select标签的引入方式 :

```
   <@button id="bbs"  size="1" value="查询" icon="search" onclick="ss();"/>

   <@button id="dd"  size="1" value="删除" icon="remove"/>

   <@button id="rr"  size="1" value="重置" icon="repeat"/>
```

![](/assets/button.png)

