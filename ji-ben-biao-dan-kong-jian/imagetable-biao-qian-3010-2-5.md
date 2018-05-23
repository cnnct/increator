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
*                 
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
            		load_data_init="queryForm"/>
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
  
* 后台写法参照demo示例，例如：

        /** 测试查询image_table表格
             * 
             * @param request
             * @return
             * @throws Exception
             */
            @RequestMapping("/query")
            @ResponseBody // 必须以json格式返回
            public ResultData queryBrchInfo(HttpServletRequest request, Model model) throws Exception {
                ResultData resultData = new ResultData(Result_Code.SUCCESS);
                // sql条件（用于sql语句中where的筛选条件，若有，则如下写法）
                if (getOper().getOrgId() != null) {
                    resultData.put("org_id", getOper().getOrgId());
                } else {
                    resultData.put("org_id", "1001");
                }
                //获取imgTable的分页
                resultData = getPageMapByImageTable(request, resultData);
                // 获取部门列表
                List<Map> tableList = new ArrayList<>();
                Map map=new HashMap<>();
                Map map1=new HashMap<>();
                Map map2=new HashMap<>();
                Map map3=new HashMap<>();
                Map map4=new HashMap<>();
                Map map5=new HashMap<>();
                Map map6=new HashMap<>();
                Map map7=new HashMap<>();
                Map map8=new HashMap<>();
                Map map9=new HashMap<>();
                Map map10=new HashMap<>();
                Map map11=new HashMap<>();
                Map map12=new HashMap<>();
                Map json=(Map)resultData.get("search");
                Long recordsTotal = 0l;
                if("pic".equals(json.get("title"))){
                	 map.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                     map.put("id", 1 );
                     map.put("title", "标题1" );
                     map1.put("src", "https://www.baidu.com/img/bd_logo1.png");
                     map1.put("id", 2 );
                     map1.put("title", "标题2" );
                     tableList.add(map);
                 	 tableList.add(map1);
                 	 recordsTotal = 2l;
                }else{
                	
                	map.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map.put("id", 1 );
                	map.put("title", "标题1" );
                	map1.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map1.put("id", 2 );
                	map1.put("title", "标题2" );
                	map2.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map2.put("id", 3 );
                	map2.put("title", "标题1" );
                	map3.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map3.put("id", 4 );
                	map3.put("title", "标题1" );
                	map4.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map4.put("id", 5 );
                	map4.put("title", "标题1" );
                	map5.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map5.put("id", 6 );
                	map5.put("title", "标题1" );
                	map6.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map6.put("id", 7 );
                	map6.put("title", "标题1" );
                	map7.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map7.put("id", 8 );
                	map7.put("title", "标题1" );
                	map8.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map8.put("id", 9 );
                	map8.put("title", "标题1" );
                	map9.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map9.put("id", 10 );
                	map9.put("title", "标题1" );
                	map10.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map10.put("id", 11 );
                	map10.put("title", "标题1" );
                	map11.put("src", "https://www.baidu.com/img/bd_logo1.png");
                	map11.put("id", 12 );
                	map11.put("title", "标题1" );
                	map12.put("src", "http://pic.sc.chinaz.com/files/pic/pic9/201401/apic3188.jpg");
                	map12.put("id", 13 );
                	map12.put("title", "标题1" );
                	tableList.add(map);
                	tableList.add(map1);
                	tableList.add(map2);
                	tableList.add(map3);
                	tableList.add(map4);
                	tableList.add(map5);
                	tableList.add(map6);
                	tableList.add(map7);
                	tableList.add(map8);
                	tableList.add(map9);
                	int start=Integer.parseInt(resultData.get("start").toString());
                	if(start>1){
                		tableList.clear();
                		tableList.add(map10);
                		tableList.add(map11);
                		tableList.add(map12);
                		
                	}
                	// 获取总记录数
                	recordsTotal = 13l;
                }
                //返回分页数据
                initPaginationByImageTable(resultData, tableList, recordsTotal);
                return resultData;
            }
    
    **注意**：返回的list<Map>中map必须包含id，src，title属性
