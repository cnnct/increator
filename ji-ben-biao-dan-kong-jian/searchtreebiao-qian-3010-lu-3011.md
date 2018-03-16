# search\_tree**标签**

#### search\_tree**标签的属性 :**
注意：remote验证需要开启同步验证属性，详细见form标签

> search\_tree标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > \***tree\_id：** 树的id
> >
> > **checkbox\_have：** 是否为复选框,默认单选
> >
> > \***sql\_key：** SQL语句对应的key , 比如：select func\_id as id,parent\_id as pId,title as name,\(case when title='角色新增' then 'true' else 'false' end\) as checked from sys\_func 
> >
> > **label：** label标签
> >
> > **sql\_condition：** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符
> >注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",search\_tree标签的默认size为5
> >
> > **cust_get_data_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和静态方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和静态方法的参数（现阶段只支持单个参数且为string类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >


#### search\_tree标签的引入方式 :

```
<@search_tree id="search" name="search_name" tree_id="search_tree" sql_key="sysfunc7" checkbox_have="true" size="6" />
```

#### search\_tree标签显示效果图 :

![](/assets/search_tree.png)

