# Button**标签**

#### button**标签的属性 :**

> button标签有8个属性分别为为id、name、size、type、class、icon、value、onclick；
>
> **其中value为必填项,下面必填项加上了\*号**；
>
> > **id ** **：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为1
> >
> > **class：** class属性
> >
> > **type : **type属性，默认为“button”
> >
> > **value \* : ** value属性主要为button显示的名字
> >
> > **icon : **icon属性为button中的图标样式，默认为“search”，可填的数值详见bootstrap官网 
> >
> > 因为当select标签为多选标签时，默认加入了“--请选择--”项
> >
> > **search\_have :** search\_have为是否需要搜索框，该属性在select\_more属性为true时可用，可以填写的值
> >
> > 为"true","false",默认false
> >
> > **sql\_key  \* ：**sql\_key属性为select标签后台执行的sql的key值，sql可以是完整的，也可以是拥有“？”占位符的sql，配合sql\_condition属性使用；
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写；
> >
> > **value \_field \*: **value\_field属性是指select标签选项option的value值是由表中哪个字段来赋值；
> >
> > **show\_field \* :** show\_field属性是指select标签选项option的text值是用表中哪个字段来赋值；
> >
> > **default\_val :** default\_val属性是指select标签的默认选中值，下标从0开始，单select\_more 属性为“true”时，可以多选，
> >
> > 如default\_val="0;2",注意分隔符；



