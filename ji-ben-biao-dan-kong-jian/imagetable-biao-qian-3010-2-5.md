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

  postformByImageTable(obj);//查询更新列表方法，obj包含属性tableId,tableSearchDataJson（详细查看demo示例）



