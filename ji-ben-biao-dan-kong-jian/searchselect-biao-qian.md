# search\_select**标签**

#### search\_select**标签的属性 :**

> search\_input标签有8个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **name ：** name属性
> >
> > \***sql\_key：** SQL语句对应的key,这里支持多条sql语句以“；”分隔
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

>> **select_item ：**select的option选项

#### search\_select标签的引入方式示例 :

```
<@search_input 
    id="searchOrgName" 
    name="searchOrgName_name" 
    sql_key="org_name3" 
    show_item="org_id,org_name" 
    show_value="org_name" 
    hidden_value="org_id" 
    size="3" 
    select_item="栏目1,栏目2"/>
```
#### search\_select标签的引入方式 示例:


#### search\_select标签显示效果图 :



