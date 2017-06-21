# 级联**标签组**

#### 级联标签组：

> > 级联标签包含两个标签，分别为cas\_select\_parent（级联顶级标签）、cas\_select\_child（级联子孙级标签）

#### cas\_select\_parent**标签的属性 :**

> cas\_select\_parent标签有8个属性分别为为id、name、size、label、sql\_key、value\_field、show\_field、child\_info；
>
> **其中sql\_key、value\_field、 show\_field、child\_info为必填项,下面必填项加上了\*号**；
>
> > **id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",cas\_select\_parent标签的默认size为5
> >
> > **label ：** label为cas\_select\_parent标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **\* sql\_key  ：** sql\_key属性为cas\_select\_parent标签后台执行的sql的key值；
> >
> > **\* value \_field ：** value\_field属性是指cas\_select\_parent标签选项option的value值是由表中哪个字段来赋值；
> >
> > **\* show\_field ：** show\_field属性是指cas\_select\_parent标签选项option的text值是用表中哪个字段来赋值；
> >
> > **\* child\_info ：** child\_info属性是cas\_select\_parent标签记录下一级的信息的属性；
> >
> > 如child\_info="child;sysfunc3;TITLE;FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值**

#### cas\_select\_child**标签的属性 :**

> cas\_select\_child标签有5个属性分别为为id、name、size、label、child\_info；
>
> **其中id为必填项,下面必填项加上了\*号**；
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",cas\_select\_child标签的默认size为5
> >
> > **label ：** label为cas\_select\_child标签的前缀标签属性,如label="name;true;2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号,即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name;true;2" ； label="name;true" ；
> >
> > label="name" ；label="name;;2" 即三个值都非必填项
> >
> > **child\_info  ：** child\_info属性是cas\_select\_child标签记录下一级的信息的属性；
> >
> > 如child\_info="child;sysfunc3;TITLE;FUNC\_ID",其中第一项为子级的id，第二项为子级加载数据要执行的sql\_key的值，第三
> >
> > 项为子级option的text值是用表中哪个字段来赋值，第四项为子级option的value值是由表中哪个字段来赋值，**四项都为必填值，但是如果该级为最后一级则child\_info属性不必存在**

#### 级联标签的引入方式 :

```
       <@cas_select_parent  label="级联1：;false" id="parent" name="parent" sql_key="sysfunc1" show_field="TITLE" value_field="FUNC_ID"  child_info="child;sysfunc3;TITLE;FUNC_ID"/>

       <@cas_select_child  label="级联2：;false" id="child"   name="child"  child_info="grandson;sysfunc5;TITLE;FUNC_ID"/>

       <@cas_select_child  label="级联3：;false" id="grandson"  name="grandson"  child_info="padson;sysfunc6;TITLE;FUNC_ID"/>

       <@cas_select_child  label="级联4：;false" id="padson"  name="padson"/>
```

#### 对应sql语句 ：

![](/assets/cas_select_sql.png)

#### 显示结果 :

![](/assets/casSelect.png)

