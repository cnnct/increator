# Button**标签**

#### button**标签的属性 :**

> button标签有9个属性分别为为id、name、size、type、class、icon、value、onclick、data\_target；
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
> > **\* value :** value属性主要为button显示的名字
> >
> > **icon :** icon属性为button中的图标样式，默认为“search”，可填的数值详见bootstrap官网
> >
> > **onclick :** onclick属性
> >
> > **data\_target :** data\_target属性为绑定模态框时使用，值为指向的modal框的id值 data\_target="add-modal"
> >
> > **auth\_key【1.1】:** 权限属性，auth\_key="brch\_add",非必填项，如果没有该属性，则为非权限按钮，如果存在，
> >
> > 则会根据sys\_func表去匹配url字段判断该角色是否存在权限
> >
> > **position【1.1】: **按钮position属性,用于相对位置\(left：居左、center：居中、right：居右\)
>>
> > **check_resubmit【1.3】: ** 按钮防止重复提交属性，默认false，为true时检查重复提交

#### button标签的引入方式 :

```
   <@button id="bbs"  size="1" value="查询" icon="search" onclick="ss();"/>

   <@button id="dd"  size="1" value="删除" icon="remove"/>

   <@button id="rr"  size="1" value="重置" icon="repeat"/>
```

#### button标签的显示结果 :

![](/assets/button.png)

#### button图标使用，icon="xxxxxx"，值取样式表名称的“-”横线后的字符串，如下图所示

[http://v3.bootcss.com/components/](http://v3.bootcss.com/components/)

![](/assets/icon-font03.png)



