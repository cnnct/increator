# toast**标签**

#### toast**标签的属性 :**

> toast标签有6个属性分别为为id、name、size、checkbox\_have、tree\_id、sql\_key，**其中id、tree\_id、sql\_key为必填项**
>
> > **id  \* ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为5
> >
> > **checkbox\_have ：** 为是否有复选框，默认false
> >
> > **tree\_id \* ：** tree树对象的id
> >
> > **sql\_key \* ：** sql\_key属性为select标签后台执行的sql的key值

#### tree标签的引入方式 :

```
<@tree size="12" id="but2" tree_id="tree2" name="valuetree2" sql_key="sysfunc8" checkbox_have="true"/>
```



