# Select**标签**

#### select**标签的属性**

>select标签有12个属性分别为为id、name、size、readonly、label、select\_more、choice\_have、

>search\_have、sql\_condition、sql\_key、value\_field、show\_field；其中id、sql\_key、value\_field、

>show\_field为必填

>项,下面必填项加上了\*号；

> id \* ： id属性  

> name ： name属性
>
> size ： size为尺寸标签,可以填的数值范围为（1-12）,如size="6",select标签的默认size为5
>
> readonly ： readonly为只读属性,可以填写的数值为"true","false",默认为false
>
> label : label为select标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值为

> 前缀标签的名字；

> 第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,可填的数值范围为（1-12）,默认尺寸

> 为1

> 1；引入方式：label="name;true;2" ; label="name;true" ; label="name" label="name;;2" 即三个值都

> 非必填项

> select\_more : select\_more为是否多选,可以填的数值为"true","false",默认为false，和choice\_have、

> search\_have属性配合使用

> choice\_have : choice\_have为是否需要第一项加入“--请选择--”这一项,可以填写的数值为"true","false",

>默认值

> 为false,

> 如果select\_more属性为true时,choice\_have必须为false,因为当select标签为多选标签时，默认加入了“--前

> 选择--”项

> search\_have : search\_have为是否需要搜索框，该属性在select\_more属性为true时可用，可以填写的值

> 为"true","false",默认false

> sql\_key  ：sql\_key为select标签后台执行的sql的key值，

> #### select标签的引入方式见form标签，必须配合form标签使用



