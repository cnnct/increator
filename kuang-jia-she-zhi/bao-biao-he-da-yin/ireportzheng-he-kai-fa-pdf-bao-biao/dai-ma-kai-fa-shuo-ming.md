# 注意：

> * ###### ireport报表打印应用于对一些有查询结果集的报表的打印。若仅只是凭证页或单张报表打印，可详见“[单面凭证报表打印开发](/kuang-jia-she-zhi/bao-biao-he-da-yin/dan-ye-ping-zheng-bao-biao-da-yin-kai-fa.md)”章节。
> * ###### 由于是结结果集的打印，一般数据量会有些大，因此本功能未插入sys\_report表保存历史打印数据，不会在凭证重打功能中显示查询。

# 第一步，使用ireport工具绘制报表

> ireport使用说明详见“[ireport使用说明](/kuang-jia-she-zhi/bao-biao-he-da-yin/ireportzheng-he-kai-fa-pdf-bao-biao/ireportshi-yong-shuo-ming.md)”，绘制完成的报表文件后缀名为jrxml，并同步编译成二进制报表文件，后缀名为jasper，两个文件一并拷贝到web目录中的reportfiles中，文件命名规则同普通页面命名相同，英文小写+下划线组合，能根据文件名就能看出是什么报表。

# 第二步，代码实现

以下以网点报表为例

* #### 页面代码实现

> 1、根据业务需要增加打印按钮，注意按钮图标使用：icon="print"
>
> 2、增加报表页的iframe，注意属性：report\_window="true"
>
> 3、增加弹出报表页的脚本，同其它打开窗口页脚本类似
>
> ```
> <@table_toolbar name="查询结果" size="8" >
>     <@button  value="新增" data_target="modal_add" icon="plus"/>
>     <@button  value="批量激活" onclick="activeAndCancel('active','mytable')" icon="ok-sign"/>
>     <@button  value="批量注销" onclick="activeAndCancel('cancel','mytable')" icon="remove-sign"/>
>     <@button  value="打印" onclick="showReport()" icon="print"/>
> </@table_toolbar>
>
> <!-- ===================== 打印框 ===================== -->
> <@modal_iframe id="modal_print" report_window="true" modal_title="打印" class="modal-lg"/>
>
> <#-- 报表打印 -->
> function showReport() {
>     $("#modal_print").modalShow("/sys/auth/brch/showReport");
> }
> ```
>
> 效果如下图所示![](/assets/report_02.png)

* #### ctrl代码实现

> 1、改造原来的列表查询方法，重点注意getPageMap方法与其它不需要报表的方法有所不同
>
> 2、增加报表显示的方法代码，大体步骤
>
> > ①指定报表文件路径
> >
> > ②指定了表格式，默认为pdf
> >
> > ③指定数据源，默认使用原始查询列表的条件进行重新查询
> >
> > ④设置报表中其它所需要的自定义参数，一般是指p\_开头的变量
> >
> > ⑤返回视图页，一般固定为“reportView”
>
> ```
>     /**
>      * 获取部门信息列表
>      * @param request
>      * @return
>      * @throws Exception 
>      */
>     @RequestMapping("/query")
>     @ResponseBody //必须以json格式返回
>     public ResultData queryBrchInfo(HttpServletRequest request) throws Exception {
>         ResultData resultData = new ResultData(Result_Code.SUCCESS);
>         // sql条件（用于sql语句中where的筛选条件，若有，则如下写法）
>         resultData.put("org_id", getOper().getOrgId());
>         //①分页参数
>         //②并将参数放入缓存中，供报表使用，其中第三个入参url是用于jasper打印，需要额外增加的入参
>         resultData = getPageMap(request,resultData,"/sys/auth/brch/query");
>         //获取部门列表        
>         List<Map> brchList = brchServ.getBrchList(resultData);
>         // 获取总记录数
>         Long recordsTotal = brchServ.getBrchCount(resultData);
>         // 返回数据，调用此方法
>         initPagination(resultData, brchList, recordsTotal);
>         return resultData;
>     }
>     
>     
>     /**
>      * 测试报表用
>      * @param request
>      * @return
>      * @throws Exception
>      */
>     @RequestMapping("/showReport")
>     public String showReport(HttpServletRequest request, Model model) throws Exception {
>         //①动态指定报表模板url
>         model.addAttribute("url", "demo/brch_list.jasper");
>         
>         //②指定报表格式
> //        model.addAttribute("format", "pdf"); // 若不设置此属性，则默认pdf,报表格式,html,xls,pdf，pdf效果最好
>         
>         //③数据源，先查询条件，可从缓存中获取，也可重新赋值
>         Map reportMap=super.getTableSearchData("/sys/auth/brch/query");
>         model.addAttribute("jrMainDataSource", brchServ.getBrchList(reportMap));
>         
>         //④其它参数
>         reportMap.put("p_Title", "我是网点报表");
>         reportMap.put("p_Auditor",super.getOperId());
>         reportMap.put("p_Creator",super.getOperId());//从session中取当前操作员
>         model.addAllAttributes(reportMap); // 其它参数
>
>         //⑤返回视图页
>         return "reportView"; // 对应jasper-views.xml中的bean id
>     }
> ```



