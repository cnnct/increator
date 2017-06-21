**\*\*\# tree**标签\*\*

#### tree**标签的属性 :**

> tree标签有6个属性分别为为id、name、size、checkbox\_have、tree\_id、sql\_key，**其中id、tree\_id、sql\_key为必填项**
>
> > **\* id ：** id属性
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
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE;session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；

#### tree标签的引入方式 :

```
<@tree size="12" id="but2" tree_id="tree2" name="valuetree2" sql_key="sysfunc8" checkbox_have="true" sql_condition="session.operId"/>
```

#### 对应sql语句 :

![](/assets/tree_sql.png)

```
SELECT
    sf.FUNC_ID AS id,
    sf.PARENT_ID AS pId,
    sf.TITLE AS name,
    (
        CASE
        WHEN sf.FUNC_ID IN (
            SELECT
                srf.FUNC_ID
            FROM
                sys_role_func srf,
                sys_role sr,
                sys_oper_role sor
            WHERE
                srf.ROLE_ID = sr.ROLE_ID
            AND     
                sor.ROLE_ID = sr.ROLE_ID
            AND      
                sor.OPER_ID = ?
        ) THEN
            'true'
        ELSE
            'false'
        END
    ) AS checked
FROM
    sys_func sf
```

**上图中红色别名必须有，且区分大小，分别对应 : 树节点的id，父级id，和显示的text名**

#### 显示结果 :

![](/assets/tree.png)

#### tree的数据重新加载方法 :

```
        treeReload(treeId,treeData);//js代码
```

#### tree获取被勾选的节点的id的方法 :

```
        getCheckedNodesIds(treeId);//js代码，返回数组
```

#### tree获取被勾选的节点的text的方法 :

```
        getCheckedNodesText(treeId);//js代码，返回字符串，以","分割
```



