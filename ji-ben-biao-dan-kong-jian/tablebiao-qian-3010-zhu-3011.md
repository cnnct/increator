# table组合标签

---

#### **query\_bar标签：**

* query\_bar标签有1个属性为id；query\_bar配合table标签使用，类似于form标签

```
    <@query_bar id="queryForm">
        <@form_group class="row">
               <@input label="部门编号" name="brchId"  size="2"  />
               <@input label="部门名称" name="brchName"  size="2"  />
               <@button  value="查询" onclick="queryInfo()" auth_key="brch_query"/>
        </@form_group>
    </@query_bar>
```

#### **table\_toolbar标签：**

* table\_toolbar标签有1个属性为name；table\\_toolbar配合table标签使用，在table标签前使用，用于包裹操作表格的工具的工具栏必须配合table标签使用，在引用table标签之前引用

```
    <@table_toolbar name="查询结果">
        <@button value="新增" data_target="modal_add" icon="plus"/>
        <@button value="批量激活" onclick="activeAndCancel('active','mytable')" icon="ok-sign"/>
        <@button value="批量注销" onclick="activeAndCancel('cancel','mytable')" icon="remove-sign"/>
    </@table_toolbar>
```

#### **table标签：**

* 引入表格栏 **table** （其他控件参看**基本表单控件**和**扩展表单控件**），表格控件的使用包含在此例中
* ```html
  <@table url="${base}/oper/query"
                 thead=[
                     [
                        {"name":"一级标题"},
                        {"name":"二级标题","colspan":"2"},
                        {"name":"三级标题","colspan":"2"}
                    ],
                    [
                        {"name":"编号"},
                        {"name":"名称"},
                        {"name":"机构"},
                        {"name":"状态"},
                        {"name":"级别"}
                    ]
                ]
                fields="id,oper_id,oper_name,org_name,brch_name,oper_state,oper_level"
                translate={"oper_state":"STATE", "oper_level":"OPER_LEVEL"}
                idtype="radio"
                operate="true"
                btn=[
                       {"name":"detail","onclick":"viewDetail(this)"},
                       {"name":"edit","auth_key":"brch","onclick":"editItem(this,'mytable')"},
                       {"name":"active","cust_label":"启    用","onclick":"activeItem(this,'mytable')"},
                       {"name":"cancel","auth_key":"brch_cancel","cust_label":"禁用","onclick":"cancelItem(this,'mytable')"},
                       {"name":"delete","onclick":"delItem(this,'mytable')"}
                    ]
                cust_btn=[
                        {
                         "name":"test1",
                         "onclick":"doTest('sd')",
                         "text":"自定义",
                         "icon":"saved",
                         "color":"success",
                         "auth_key":"brch_cust",
                          "dynswitch":{"dynbind_field":"brch_state","show_condition":["0",“1”]}
                         }]
                sort=["oper_id", "oper_name"]
                img_fields={"img_wrap":"img"}
                id="mytable"
                merge_cells=[
                    {"coordinate":"3,0","rowspan":"10"},
                    {"coordinate":"4,0","rowspan":"10"}
                ]
                callback="setPanelData"
                width="120"
                is_static="false"
                />
  <!-- 所有提交的url地址的前缀都要加上 ${base}
  1. 表格控件必须的三个参数：url、thead、fields
  2. *url： 提交的后台地址 
  3. *thead【1.2】： 表头显示的字段名（不包括第一列的id列），thead在【1.2】以后支持多级表头，每一列标题头支持3个属性，name属性指定列名，rowspan属性支持指定标题头占用的行数，默认值为1，colspan属性支持指定标题头占用的列数，默认值为1
  4. *fields：sql语句中显示的字段名
  5. translate：待转义的字段，格式为json格式![](/assets/table3.png)
  6. idtype：id列形式（单选框 radio、复选框 checkbox），默认复选框。
  7. operate：是否显示操作列，true 显示，false 不显示
  8. btn【1.1】：显示的按钮，目前有5个固定的常用按钮：
     detail 查看详情，edit 修改，delete 删除，active 激活，cancel 注销，显示按钮必须开启操作栏
     每个按钮有三个属性，name属性只有以上六种值，auth_key为权限属性，匹配sys_func表中的url，cust_label属性为自定义按钮的名字，存在默认名，onclick属性绑定执行的方法**必填**
  9. cust_btn【1.1】:cust_btn属性是除了以上常用按钮的自定义按钮,五项属性中name属性和onclick属性为必填项，且onclick的值现在只支持
      "doTest('sd')"这种传参方式，不支持'doTest("sd")'方式，text属性为button的显示值，icon属性为图标，默认为搜索图标，
      color属性为颜色属性，可以填写的值为"success"、"danger"、"info"、"warning"、"primary"，默认为蓝色,auth_key为权限属性，匹配sys_func表中的url,
      dynswitch为动态切换自定义属性，其中还包含三个属性，分别为dynbind_field指定绑定字段，对应table标签中fields中的值，show_condition属性为指定显示按钮的情况，
      值为数组，如上"show_condition":["0","1"],指当在sys_code表中valuecode为“0”或“1”时显示，对应的还存在noshow_condition属性为不显示的情况，
      show_condition和noshow_condition属性不能同时使用，同时存在时遵循show_condition属性
  10. sort：支持排序功能的字段，默认除了id列和操作列外所有字段都支持
  11. img_fields【1.1】:支持缩略图功能，img_fields={"img_wrap":"img"},"img_wrap"为缩略图字段，"img"为原图字段,点击缩略图弹出原图
  12. id【1.2】:指定表格id，【1.2】以后页面支持多表格，若未指定id属性时，id默认值为"mytable"，因此在多表格并存时，只能有一个表格可以不指定id。
  13. merge_cells【1.2】：合并单元格属性，【1.2】以后表格支持单元格合并属性，单元格合并有3个属性，coordinate属性指定操作合并的单元格坐标（x,y），rowspan指定合并的行数，默认值为1，colspan属性指定合并的列数，默认值为1，注意已经被合并占用的单元格不可以重复合并
  14. paginate【1.2.3】：paginate属性为是否分页属性，默认为true（开启分页）
  15. load_data_init【1.2.3】：load_data_init属性为是否初始化加载数据开关属性，默认为true（首次进页面加载数据）
  16. callback【1.2.3】：该属性为表格的附加回调方法，在加载完表格后，会调用指定的方法，如：callback="setPanelData"
  ，注意：该方法必须在表格加载前被定义
  17. width【1.2.3】:该属性为表格的宽度属性，默认为100
  18. 表格若不需要id列，fields 中去掉 id 字段，同时后台 sql 也去掉 id 字段：如下
      fields="oper_id,oper_name,org_name,brch_name,oper_state,oper_level"
  19. no_search_sm【1.3】，查询无记录时，提示区域大小:true/false，默认false正常大图显示。可用于表格下方还有组合用的面板场景使用。
  20. is_static【1.4】，设置是否为静态表格，静态表格为不与后台数据动态交互的表格，可以手动新增数据和删除数据，详细例子见如下小章节说明。
  备注：存在id列的情况下，首字段 id 固定，mapper 中提供的 sql 语句必须提供 id 字段名（详细见后续 mapper 语句编写）
  ```
* 表格数据显示例子如下图：  
  ![](/assets/table.png)![](/assets/table2.png)
* 表格多级表头和合并单元格示例图：
  ![](/assets/table3.png)
* 获取表格相关数据：
* ```js
  getTable(tableId);//获取表格对象

  getTableRows(tableId);//获取表格当前页行数据

  getSelectedTableRows(tableId);//获取表格当前页选中行数据

  getTableRowById(rowId,tableId);//根据rowId获取行数据,rowId值

  getCodeName(value,type,tableId);//获取翻译的name值，从sys_code表中获取

  getCodeValue(name,type,tableId);//获取翻译的value值，从sys_code表中获取
  
  removeSelectedTableRows(tableId);//删除当前表格所有勾选的行数据，只适用于静态表格

  removeTableRow(obj,tableId);//删除当前行数据，只适用于静态表格,obj为当前tr标签包含的元素
  
  addTableRow(obj,tableId);//新增表格行数据，只适用于静态表格,obj为传入新增的行数据
  
  例:getCodeName("0","STATE","mytable");//值为"注销"

  /**
  * ajax表单提交，只针对表格
  * @param url 提交地址
  * @param formId 表单id，可为空
  * @param convertName 需转换的name属性，可为空，例子："role1.id,role2.id ..."
  * @param modalId form表单提交时的modalId
  * @param tableSearchDataJson 表格查询所需的过滤数据，表格查询时不能为空
  * @param tableId 表格Id值，必须传
  * @param updateTableUrl 【1.2.3】如果要修改表格加载数据的url地址加入这一项
  * @param closeModal 【1.2.3】是否在操作成功后关闭窗口，默认true
  * @param isFnDrawCurrentTable 这里为了支持子modal框可以加入表格的功能，需要指定是否处理完数据后刷新的是当前表格还是父级表格，默认：先去找父级表格刷新，true：刷新当前表格
 * @param isFnDrawParentTable 这里为了支持子modal框可以加入表格的功能，需要指定是否处理完数据后刷新的是当前表格还是父级表格，默认：先去找父级表格刷新，true：刷新父级表格
  */
    postform({
            "tableId":"mytable",
            "url":"${base}/sys/auth/brch/save/add",
            "formId":"add_form",
            "modalId":"modal_add",
            "closeModal":"false"
        });
  ```

* 加载静态表格示例：
```html
       <@init_page>
	<#--加载静态表格-->
	    <@table_toolbar name="查询结果" size="4" >
			<@button id="addRow" value="测试给表格添加行" size="2" onclick="addRow()"/>
			<@button id="removeTableRow" value="删除选中的表格数据" size="2" onclick="removeSelectedRow()"/>
			<@button id="getRowData" value="测试获取表格选中行的数据" size="2" onclick="getTableData()"/>
	</@table_toolbar>
	<@table 
            thead=[
            	[
	            	{"name":"编号"},
	            	{"name":"名称"},
	            	{"name":"上级部门"},
	            	{"name":"创建人"},
	            	{"name":"状态"}
            	]
            ]
            operate="true"
            fields="id"
            btn=[
	            {"name":"delete","onclick":"removeRow(this,'example')","auth_key":"brchDelete"}
            ]
			id="example"
			is_static="true"
            />
</@init_page>
<script>
<#--测试给静态表格加行-->
function addRow() {
	var counter=1;
 	var addRow=[
			'10010101',//复选框id
			counter +'.2',
			counter +'.3',
			counter +'.4',
			counter +'.5',
			counter +'.6'
		];
	addTableRow(addRow,"example");

} ;
<#--测试获取表格行数据-->
function getTableData(){
	var sdk=getSelectedTableRows("example");
	var sdf=getTableRows("example");
	console.log(sdf);
	console.log(sdk);
}


<#--测试删除表格数据-->
function removeRow(obj,tableId){
	removeTableRow(obj,tableId);
}
<#--测试删除选中的行数据-->
function removeSelectedRow(){
	removeSelectedTableRows('example');
}
</script>
```
