# **table\_toolbar标签**

#### **table\_toolbar标签的属性：**

table\_toolbar标签属性如下：table\_toolbar配合table标签使用，在table标签前使用， 用于包裹操作表格的工具的工具栏必须配合table标签使用

>>   name: name属性

>>   size【1.2】: size属性，在【1.2】版本后加入size属性

>>   page_change【2.1】: page_change属性为加载分页选择器属性，有lable属性和default_val属性，
>>   引入方式如：page_change={"label":"每页显示","default_val":"20" }，default默认10

* 标签引入方式：
		<@table_toolbar name="查询结果" size="2" page_change={"label":"每页显示","default_val":"20" }>
			<@button  value="新增" data_target="modal_add" icon="ext_assessedbadge" />
			<@button  value="打印" onclick="showReport()" icon="print"/>
			<@button  value="导入" data_target="modal_import" />
			<@button  value="测试左侧导航菜单" onclick="doTest()" size="2"/>
			<@button id="toChildTableIndex" value="测试子表格和父级表格的数据交互" size="3" onclick="toChildTableIndex()" />
			<@button id="toStaticTableIndex" value="测试静态表格" size="2" onclick="toStaticTableIndex()" />
	        <@button  value="批量激活" onclick="activeAndCancel('active','mytable')" icon="ok-sign"  size="2"/>
			<@button  value="批量注销" onclick="activeAndCancel('cancel','mytable')" icon="remove-sign"  size="7"/>
		</@table_toolbar>



