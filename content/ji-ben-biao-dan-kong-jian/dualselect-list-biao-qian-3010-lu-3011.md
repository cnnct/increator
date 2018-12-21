# dual\_select\_list**标签**

#### dual\_select\_list**标签的属性 :**

注意：remote验证需要开启同步验证属性，详细见form标签

> dual\_select\_list标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > **height ：**高度，即html中的高度属性，单位为px
> >
> > \***sql\_key：** SQL语句对应的key , 前一句查询所有记录 , 后一句查询已选择记录 , 比如：select org\_id,org\_name from bs\_pay\_org;select org\_id,org\_name from bs\_pay\_org where state is not null
> >
> > \***show\_field：** 选项显示的名称
> >
> > \***value\_field：** 选项的值
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE;session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符  
> > 注意：【1.4】版本后分隔符由“，”替换成为“&&&”  

> > **readonly**：是否可选
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",dual\_select\_list标签的默认size为12
> >
> > **cust_get_data_clazz【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.1】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为Map类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >


#### dual\_select\_list标签的引入方式 :

```
<@dual_select_list id="dualSelectOrgName" name="dualSelectOrgName_name" show_field="org_name" value_field="org_id" sql_key="org_name2" size="8" />
```

#### dual\_select\_list标签显示效果图 :

![](/assets/dual_select_list.png)

