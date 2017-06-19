# input\_tree**标签**

#### input\_tree**标签的属性 :**

> input\_tree标签有6个属性分别为为id、name、size、checkbox\_have、tree\_id、sql\_key，**其中id、tree\_id、sql\_key为必填项**
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

>> **sql_condition :** sql_condition属性用于配合sql_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql_condition="ACC_RECHG_TYPE;session.operId",其中‘ACC_RECHG_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；



#### input\_tree标签的引入方式 :

```
<@input_tree label="单选树" size="4" id="but" tree_id="tree" name="valuetree" sql_key="sysfunc7" />

<@input_tree label="多选树" size="5" id="but1" tree_id="tree1" name="valuetree1" sql_key="sysfunc7" checkbox_have="true"/>
```

#### ![](/assets/input_tree .png)input\_tree的数据重新加载方法 :

```
        treeReload(treeId,treeData);//js代码
```

#### input\_tree获取被勾选的节点的id的方法 :

```
        getCheckedNodesIds(treeId);//js代码，返回数组
```

#### input\_tree获取被勾选的节点的text的方法 :

```
        getCheckedNodesText(treeId);//js代码，返回字符串，以","分割
```



