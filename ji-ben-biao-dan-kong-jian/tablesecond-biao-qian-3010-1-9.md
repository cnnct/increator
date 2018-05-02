# table_second**标签**

####table_second**标签的属性 :**
**注意：该属性组件不支持ie8，ie9等浏览器**

> table_second标签为含第二样式的表格标签，相对于table标签，功能比较单一，但是比较灵活，支持表格行数据的拖拽，新增行数据，修改行内数据，删除数据，含有的属性如下：
** 注意【2.1】：由于freemarker的数组和对象类型不能解析el表达式，所以为了配套普通select类型的sql_key执行，在【2.1】版本后，支持属性sql_condition的扩展，详情见下面标签引入示例**

>
> > ***id ：** id属性
> >
> > ***url：** 加载表格数据的url属性
> >
> > **width：** 宽度属性，默认100
> >
> > **height【2.0】：** 高度属性，默认全部展示，可填数值
> >
> > ***fields:** 表格的加载字段属性，为数组对象，单个字段对象包含属性：name(加载的字段名)，title(字段标题),type(编辑时的类型，现支持text,textarea,code_select,myDateField(时间)，注意当为code_select类型时必须指定code_type,当type为空且不存在时，将冻结列),width(宽度，默认100)，position为列的位置，默认center，可填值center，left，right,【2.0】版本后调整type有select，code_select项，code_select需要指定code_type,如果是select需要指定sql_key（配套sql_condition），value_field，show_field
> >
> > **editor_flag:【2.0】** 编辑功能开关，默认false，即编辑功能冻结，当为true时可以新增行，修改行，删除行，移动行
> >
> > **format:【2.0】** 表格的时间匹配格式，默认为yyyy-MM-dd HH:mm:ss
> > * p：子午线（“am”或“pm”） - 根据区域设置文件
> > * P：子午线大写（“AM”或“PM”） - 根据区域设置文件
> > * s：没有前导零的秒
> > * ss：秒，带前导零的2位数字
> > * i：没有前导零的分钟
> > * ii：分钟，带前导零的2位数字
> > * h：小时无前导零 - 24小时格式
> > * hh：小时，2位数字，带前导零 - 24小时格式
> > * H：小时无前导零 - 12小时格式
> > * HH：小时，2位数字带前导零 - 12小时格式
> > * d：没有前导零的月份的日
> > * dd：月份的日，带前导零的2位数字
> > * m：没有前导零的月份的数字表示
> > * mm：月份的数字表示，带前导零的2位数字
> > * M：一个月的短文本表示，三个字母
> > * MM：一个月的全文表示，例如1月或3月
> > * yy：一年的两位数表示
> > * yyyy：一年的全数字表示，4位数字
>>
>> ** search_have:【2.0】** 是否拥有搜索功能，默认false
>>
>> ** delete_message:【2.1】** 删除提示，默认提示“确定要删除记录？”






#### table_second标签的引入方式 :
* 1.首先加入标签，引入必要方法：
![](/assets/table_second9.png)
![](/assets/table_second10.png)
![](/assets/table_second2.png)
![](/assets/table_second3.png)

#### table_second标签的显示结果 :

![](/assets/table_second11.png)
#### 后台加载数据写法：
![](/assets/table_second5.png)

#### 提供的可供调用的js方法：


