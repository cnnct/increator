# table组合标签

---

#### **table\_toolbar标签：**

* table\_toolbar标签有1个属性为name；table\\_toolbar配合table标签使用，在table标签前使用，用于包裹操作表格的工具的工具栏必须配合table标签使用，在引用table标签之前引用

```
    <@table_toolbar name="查询结果">
        <@button value="新增" data_target="modal_add" icon="plus"/>
        <@button value="批量激活" onclick="activeAndCancel('active')" icon="ok-sign"/>
        <@button value="批量注销" onclick="activeAndCancel('cancel')" icon="remove-sign"/>
    </@table_toolbar>
```

#### **table标签：**

* 引入表格栏 **table** （其他控件参看**基本表单控件**和**扩展表单控件**），表格控件的使用包含在此例中
* ```html
  <@table url="${base}/oper/query"
                thead="编号,姓名,机构,部门,状态,级别"
                fields="id,oper_id,oper_name,org_name,brch_name,oper_state,oper_level"
                translate={"oper_state":"STATE", "oper_level":"OPER_LEVEL"}
                idtype="radio"
                operate="true"
                btn=[
                        {"name":"detail"},
                        {"name":"edit","auth_key":"brch_edit"},
                        {"name":"active","cust_label":"启用"},
                        {"name":"cancel","auth_key":"brch_cancel","cust_label":"禁用"},
                        {"name":"delete"}
                    ]
                cust_btn=[{
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
                />
  <!-- 所有提交的url地址的前缀都要加上 ${base}
  1. 表格控件必须的三个参数：url、thead、fields
  2. url： 提交的后台地址 
  3. thead： 表头显示的字段名（不包括第一列的id列）
  4. fields：sql语句中显示的字段名
  5. translate：待转义的字段，格式为json格式
  6. idtype：id列形式（单选框 radio、复选框 checkbox），默认复选框。
  7. operate：是否显示操作列，true 显示，false 不显示
  8. btn：显示的按钮，目前有5个固定的常用按钮：
     detail 查看详情，edit 修改，delete 删除，active 激活，cancel 注销，显示按钮必须开启操作栏
     每个按钮有三个属性，name属性只有以上六种值，auth_key为权限属性，匹配sys_func表中的url，cust_label属性为自定义按钮的名字，存在默认名
  9. cust_btn:cust_btn属性是除了以上常用按钮的自定义按钮,五项属性中name属性和onclick属性为必填项，且onclick的值现在只支持
      "doTest('sd')"这种传参方式，不支持'doTest("sd")'方式，text属性为button的显示值，icon属性为图标，默认为搜索图标，
      color属性为颜色属性，可以填写的值为"success"、"danger"、"info"、"warning"、"primary"，默认为蓝色,auth_key为权限属性，匹配sys_func表中的url,
      dynswitch为动态切换自定义属性，其中还包含三个属性，分别为dynbind_field指定绑定字段，对应table标签中fields中的值，show_condition属性为指定显示按钮的情况，
      值为数组，如上"show_condition":["0","1"],指当在sys_code表中valuecode为“0”或“1”时显示，对应的还存在noshow_condition属性为不显示的情况，
      show_condition和noshow_condition属性不能同时使用，同时存在时遵循show_condition属性
  10. sort：支持排序功能的字段，默认除了id列和操作列外所有字段都支持
  11.img_fields:支持缩略图功能，img_fields={"img_wrap":"img"},"img_wrap"为缩略图字段，"img"为原图字段,点击缩略图弹出原图
  12. 表格若不需要id列，fields 中去掉 id 字段，同时后台 sql 也去掉 id 字段：如下
      fields="oper_id,oper_name,org_name,brch_name,oper_state,oper_level"
  备注：存在id列的情况下，首字段 id 固定，mapper 中提供的 sql 语句必须提供 id 字段名（详细见后续 mapper 语句编写）
  -->
  ```
* 表格数据显示例子如下图：  
  ![](/assets/table.png)![](/assets/table2.png)

* 获取表格相关数据

* ```js
  getTable();//获取表格对象

  getTableRows();//获取表格当前页行数据

  getSelectedTableRows();//获取表格当前页选中行数据

  getTableRowById(rowId);//根据rowId获取行数据,rowId值

  getCodeName(value,type);//获取翻译的name值，从sys_code表中获取

  getCodeValue(name,type);//获取翻译的value值，从sys_code表中获取

  例:getCodeName("0","STATE");//值为"注销"
  ```



