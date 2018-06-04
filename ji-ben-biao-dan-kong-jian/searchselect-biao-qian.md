# search\_select**标签**

#### search\_select**标签的属性 :**

注意：remote验证需要开启同步验证属性，详细见form标签

> search\_select标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > \***sql\_key：** SQL语句对应的key
> >
> > **sql\_condition【2.6】：** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“??”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE&&&session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
> >
> > \***show\_item：** 显示的内容
> >
> > \***show\_value：** 显示的值
> >
> > \***hidden\_value：** 需要的值
> >
> > **label：** label标签
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",search\_input标签的默认size为5
> >
> > \***select\_item ：**select的option选项，对应sql\_key对应的语句
> >
> > **cust\_get\_data\_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql\_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust\_get\_data\_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql\_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为Map类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页

#### search\_select标签的引入方式示例 :

```
<@search_select 
    id="searchOrgName" 
    name="searchOrgName_name" 
    sql_key="org_name3" 
    show_item="org_id,org_name" 
    show_value="org_name" 
    hidden_value="org_id" 
    size="3" 
    select_item="栏目1,栏目2"/>
```

#### search\_select标签sql示例:

![](/assets/search_select2.png)

#### search\_select标签显示效果图 :

![](/assets/search_select3.png)

