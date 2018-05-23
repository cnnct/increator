# image_table组合标签

#### 注：表格后台查询返回到页面的List&lt;Map&gt;，由于都经过initPaginationByImageTable\(a,b,c\)方法处理，所以Map中的key都已经转为纯小写了。

#### 由此，&lt;table&gt;标签中fields等属性也应该全部小写。

---

#### **query\_bar标签：**

* query\_bar标签有属性：id，icon，title，style\_type
  > > **style\_type: **style\_type属性是用来控制query\_bar的风格样式，暂时提供"default"（默认样式），"classical"（经典样式）,"simple"\(简约样式\)  
  > > **icon **icon属性是用来控制query\_bar的标题头的图标，默认没有图标，图标设置参考button标签
  > >
  > > **title:** title属性为标题属性

query\_bar配合image_table标签使用，类似于form标签

```
    <@query_bar id="queryForm">
        <@form_group class="row">
               <@input label="标题" name="title"  size="2"  />
               <@button  value="查询" onclick="queryInfo()" auth_key="brch_query"/>
        </@form_group>
    </@query_bar>
```



#### **image_table标签：**

* 引入表格栏 **image_table** （其他控件参看**基本表单控件**和**扩展表单控件**），表格控件的使用包含在此例中
* ```html
  <@table id="mytable" 
	      url="${base}/demo/tag/query  
	      btn=[
		        {"name":"edit","onclick":"editItem()"},
	            {"name":"delete","onclick":"delItem()"}
		    ]
		  cust_btn=[
			    {
			     "name":"test1",
			     "onclick":"doTest()",
			     "icon":"saved",
			     "title":"提示"
		        }
		    ]
		load_data_init="queryForm"
                />
  <!-- 所有提交的url地址的前缀都要加上 ${base}
  1. *id:table的id属性
  2. *url： 提交的后台地址 
  3. btn：显示的按钮，目前有2个固定的常用按钮：
     edit 修改，delete 删除，每个按钮有属性：name属性只有以上两种值，auth_key为权限属性，匹配sys_func表中的url，onclick属性绑定执行的方法**必填**,版本后加入提示title属性
  4. cust_btn:cust_btn属性是除了以上常用按钮的自定义按钮,属性中name属性和onclick属性为必填项，且onclick的值现在只支持
      "doTest('sd')"这种传参方式，不支持'doTest("sd")'方式，icon属性为图标，默认为搜索图标，支持图标扩展可以使用font-increator下的图标，前缀"ext_"加图标样式名即可以使用，如"ext_assessedbadge"，详细可以参考button标签，auth_key为权限属性，匹配sys_func表中的url，提示title属性
  5. load_data_init【1.2.3】：load_data_init属性为是否初始化加载数据开关属性，默认为true（首次进页面加载数据）,【1.4】版本后，支持传入的值为“true”，“false”，或指定查询条件的formId，当值为“true”或不填该属性时，默认不带查询条件初始化加载数据，为“false”时不加载数据，为formId时，会带查询条件加载数据

* 表格数据显示例子如下图： （详情参考标签示例页） 
 ![](/assets/image_table1.png)


* 表格相关js方法：
  imageTableChangePageNum(tableId,pageNum);//跳转页码

  getTableRows(tableId);//获取表格当前页行数据

  getSelectedTableRows(tableId);//获取表格当前页选中行数据

  getTableRowById(rowId,tableId);//根据rowId获取行数据,rowId值

  getCodeName(value,type,tableId);//获取翻译的name值，从sys_code表中获取

  getCodeValue(name,type,tableId);//获取翻译的value值，从sys_code表中获取

  removeSelectedTableRows(tableId);//删除当前表格所有勾选的行数据，只适用于静态表格

  removeTableRow(obj,tableId);//删除当前行数据，只适用于静态表格,obj为当前tr标签包含的元素

  addTableRow(obj,tableId,idType);//新增表格行数据，只适用于静态表格,obj为传入新增的行数据，idType为首列勾选的样式，可填三个值：none，radio，checkbox，默认none

  tableBandClick(obj)【2.4】;//为表格指定的td位置绑定自定义的方法，如果表格中没有数据就不绑定
  其中包含tdPosition(数组类型[{}]包含需要绑定事件的td标签的坐标位置，其中子对象包含数rowIndex(行下标，   从0开始)和colIndex(列下标，从0开始)，如果不指定行，则绑定整列)和bandFunction绑定的自定义的方法名和 tableId
  调用如：  tableBandClick({"tdPosition[{"colIndex":"2"}],"tableId":"mytable","bandFunction":"daTest1"});
 */
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
  * @param isFnDrawCurrentTable【1.3】 这里为了支持子modal框可以加入表格的功能，需要指定是否处理完数据后刷新的是当前表格还是父级表格，默认：先去找父级表格刷新，true：刷新当前表格
  * @param isFnDrawParentTable 【1.3】这里为了支持子modal框可以加入表格的功能，需要指定是否处理完数据后刷新的是当前表格还是父级表格，默认：先去找父级表格刷新，true：刷新父级表格
  * @param redirectPageNum 【1.4】指定操作后指向的页码，注意页码从0开始，当该选项不传入时，默认刷新整个表格，即回到首页
  */
    postform({
            "tableId":"mytable",
            "url":"${base}/sys/auth/brch/save/add",
            "formId":"add_form",
            "modalId":"modal_add",
            "closeModal":"false"
        });
  ```


