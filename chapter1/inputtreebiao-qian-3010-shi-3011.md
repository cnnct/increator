# input\_tree**标签**

#### input\_tree**标签的属性 :**

> input\_tree标签有6个属性分别为为id、name、size、checkbox\_have、tree\_id、sql\_key，**其中id、tree\_id、sql\_key为必填项**
>
> > **id ** \* **：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为5
> >
> > **checkbox\_have : **为是否有复选框，默认false
> >
> > **tree\_id \* :** tree树对象的id
> >
> > **sql\_key \* : ** sql\_key属性为select标签后台执行的sql的key值

#### input\_tree标签的引入方式 :

&lt;@input\_tree label="单选树" size="4" id="but" tree\_id="tree" name="valuetree" sql\_key="sysfunc7" /&gt;

	&lt;@input\_tree label="多选树" size="5" id="but1" tree\_id="tree1" name="valuetree1" sql\_key="sysfunc7" checkbox\_have="true"/&gt;

