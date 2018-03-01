# table_second**标签**

####table_second**标签的属性 :**

> table_second标签为含第二样式的表格标签，相对于table标签，功能比较单一，但是比较灵活，支持表格行数据的拖拽，新增行数据，修改行内数据，删除数据，含有的属性如下：
>
> > ***id ：** id属性
> >
> > ***url：** 加载表格数据的url属性
> >
> > **width：** 宽度属性，默认100
> >
> > **height【1.9】：** 高度属性，默认全部展示，可填数值
> >
> > ***fields:** 表格的加载字段属性，为数组对象，单个字段对象包含属性：name(加载的字段名)，title(字段标题),type(编辑时的类型，现支持text,textarea,select,myDateField(时间)，注意当为select类型时必必须指定code_type,当type为空且不存在时，将冻结列),width(宽度，默认100)
> >
> > ***editor_flag:【1.9】** 编辑功能开关，默认false，即编辑功能冻结，当为true时可以新增行，修改行，删除行，移动行
> >




#### table_second标签的引入方式 :
* 1.首先加入标签，引入必要方法：
![](/assets/table_second6.png)
![](/assets/table_second2.png)
![](/assets/table_second3.png)
**注意：**需要实现的方法不能return，否则会阻断数据异步刷新
#### table_second标签的显示结果 :

![](/assets/table_second7.png)
#### 后台加载数据写法：
![](/assets/table_second5.png)

