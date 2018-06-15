# 级联**标签组**

#### 级联标签组：

> > 级联标签包含两个标签，分别为cas\_select\_parent（级联顶级标签）、cas\_select\_child（级联子孙级标签）

#### cas\_select\_parent**标签的属性 :**

> cas\_select\_parent标签有属性分别如下：
>
> **其中sql\_key、value\_field、 show\_field、child\_info为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",cas\_select\_parent标签的默认size为5
> >
> > **label ：** label为cas\_select\_parent标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **\* sql\_key  ：** sql\_key属性为cas\_select\_parent标签后台执行的sql的key值；
> >
> > **\* value \_field ：** value\_field属性是指cas\_select\_parent标签选项option的value值是由表中哪个字段来赋值；
> >
> > **\* show\_field ：** show\_field属性是指cas\_select\_parent标签选项option的text值是用表中哪个字段来赋值；
> >
> > **\* child\_info【1.2.2】 ：** child\_info属性是cas\_select\_parent标签记录下一级的信息的属性；
> >
> >（ 如child\_info="child,sysfunc3,TITLE,FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值**）
【1.3】版本后忽略上面括号部分采用如下形式：
child_info=[
									{"child_id":"parent_brch_id","sql_key":"sysbrch3","show_field":"brch_name","value_field":"brch_id","sql_condition":"1","num_for_selected":"1"}
					]  
> >其中sql_condition为sql执行时需要加入的条件，num_for_selected属性为父级选中项的值加入占位符的位置
> >注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > **default\_val :** default\_val属性是指cas\_select\_parent标签的默认选中值，该值为option的value值
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > **search\_have 【1.2.3】:** search\_have为是否需要搜索框，可以填写的值为"true","false",默认false

> > **child_sql_condition【1.3】：**该属性是为了解决el表达式在ftl数组属性中解析不了的问题，即child_info属性中的sql_condition属性被该属性替换，引入方式：child_sql_condition="${operVo.brch.brchId},2;4"，child_info属性中不同元素的sql_condition属性需要的值用‘；’分割,
注意：【1.4】版本后分隔符由“，”替换成为“&&&”,如child_sql_condition="${operVo.brch.brchId}&&&2;4"
> > **cust_get_data_clazz【2.6】：** 该功能用于支持自定义加载的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >
> > **cust_get_data_param【2.6】：** 该功能用于支持自定义加载的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和方法的参数（现阶段只支持单个参数且为Map类型）,规则示例将在下面展示，具体示例见2.0平台基础项目demo页
> >


#### cas\_select\_child**标签的属性 :**

> cas\_select\_child标签属性分别如下：
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",cas\_select\_child标签的默认size为5
> >
> > **label ：** label为cas\_select\_child标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
> >
> > **readonly ：** readonly为只读属性,可以填写的数值为"true","false",默认为false
> >
> > **child\_info 【1.2.2】 ：** child\_info属性是cas\_select\_child标签记录下一级的信息的属性；
> >
> > （如child\_info="child,sysfunc3,TITLE,FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值，但是如果该级为最后一级则child\_info属性不必存在**）
【1.3】版本后忽略上面括号部分采用如下形式：
child_info=[
									{"child_id":"parent_brch_id","sql_key":"sysbrch3","show_field":"brch_name","value_field":"brch_id","sql_condition":"1","num_for_selected":"1"}]
其中sql_condition为sql执行时需要加入的条件，注意：【1.4】版本后分隔符由“，”替换成为“&&&”
，num_for_selected属性为父级选中项的值加入占位符的位置
> **\* 以下几个属性特别注意，当级联需要默认值时下面sql\_key、value\_field、show\_field为必填项，  
> 一般情况不需要加入下面几个属性 **
>
> > ** sql\_key  ：** sql\_key属性为cas\_select\_child标签后台执行的sql的key值；
> >
> > ** value \_field ：** value\_field属性是指cas\_select\_child标签选项option的value值是由表中哪个字段来赋值；
> >
> > ** show\_field ：** show\_field属性是指cas\_select\_child标签选项option的text值是用表中哪个字段来赋值；
> >
> > **default\_val :** default\_val属性是指cas\_select\_child标签的默认选中值，该值为option的value值
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
> >
> > **search\_have 【1.2.3】:** search\_have为是否需要搜索框，可以填写的值为"true","false",默认false
> > **child_sql_condition【1.3】：**该属性是为了解决el表达式在ftl数组属性中解析不了的问题，
> >即child_info属性中的sql_condition属性被该属性替换，引入方式：child_sql_condition="${operVo.brch.brchId},2;4"，child_info属性中不同不同元素的sql_condition属性需要的值用‘；’分割，注意：【1.4】版本后分隔符由“，”替换成为“&&&”,如child_sql_condition="${operVo.brch.brchId}&&&2;4"







#### 级联标签的引入方式 :

```
       <@cas_select_parent  label="级联1：,false" id="parent" name="parent" sql_key="sysfunc1" show_field="TITLE" value_field="FUNC_ID"  child_info=[{"child_id":"child","sql_key":"sysbrch3","show_field":"TITLE","value_field":"FUNC_ID"}]/>

       <@cas_select_child  label="级联2：,false" id="child"   name="child"  child_info=[{"child_id":"grandson","sql_key":"sysfunc5","show_field":"TITLE","value_field":"FUNC_ID"}]/>

       <@cas_select_child  label="级联3：,false" id="grandson"  name="grandson"  child_info=[{"child_id":"padson","sql_key":"sysfunc6","show_field":"TITLE","value_field":"FUNC_ID"}]/>

       <@cas_select_child  label="级联4：,false" id="padson"  name="padson"/>
```

#### 对应sql语句 ：

![](/assets/cas_select_sql.png)

#### 显示结果 :

![](/assets/casSelect.png)

