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

* #### ctrl代码实现，注意示例代码中的注释解释

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
> > ④获取计算报表所需要的合计行等数据
> >
> > ⑤设置报表中其它所需要的自定义参数，包括合计行数据，一**般是指p\_开头的变量**
> >
> > ⑥返回视图页，一般固定为“reportView”
>
> 3、ctrl代码示例
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
>         // ②并将参数放入缓存中，供报表使用，
>         //    其中第三个入参是用于jasper打印，需要额外增加的入参，实际就是一个map的key
>         //    可以是任意不重复的值（需要pdf打印的功能不能重复），一般就用当前url比较好理解
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
>         //model.addAttribute("format", "pdf"); // 若不设置此属性，则默认pdf,报表格式,html,xls,pdf，pdf效果最好
>         
>         //③数据源，先查询条件，可从缓存中获取，也可重新赋值
>         //入参即为对应在的查询功能缓存的查询条件的map的key，其key值与queryBrchInfo方法中指定key为同一个
>         Map reportMap=super.getTableSearchData("/sys/auth/brch/query");
>         model.addAttribute("jrMainDataSource", brchServ.getBrchList(reportMap));
>         
>         //④取合计行，可举一反三，可计算多个合计数
>         List<Map> list=brchServ.getBrchSum(reportMap);
>         Map map=list.get(0);
>         
>         //⑤组装参数
>         reportMap.put("p_TotAmt", map.get("level_sum"));//金额合计行，从上面的查询结果中获取（举例）
>         reportMap.put("p_Title", "我是网点报表");
>         reportMap.put("p_Auditor",super.getOperId());
>         reportMap.put("p_Creator",super.getOperId());//从session中取当前操作员
>         model.addAllAttributes(reportMap); // 其它参数
>
>         //⑥返回视图页
>         return "reportView"; // 对应jasper-views.xml中的bean id
>     }
> ```
>
> 4、sqlmapper.xml代码示例，注意mysql和oracle的语法不同，详见下方代码注释说明：
>
> ```
>     <!-- 获取部门列表，mysql语法 -->
>     <!-- 其中 (@rownum:=@rownum+1)as rn 表示行号，注意oracle写法不一样-->
>     <select id="getBrchList" parameterType="Map" resultType="Map" databaseId="mysql">
>         select (@rownum:=@rownum+1)as rn, a.brch_id as id, a.brch_id, a.brch_name,a.img_wrap,a.img,
>         case when a.parent_brch_id = '' then '-'
>         else (select brch_name from sys_branch where brch_id=a.parent_brch_id)
>         end parent_brch_id, a.open_oper_id,a.brch_state,
>         o.img organ_img,
>         <!-- 测试报表的格式化字符串，格式化2位小数，若空值则为0 -->
>         CAST(IFNULL(a.BRCH_LEVEL,0) AS DECIMAL(10,2)) AS level
>         from sys_branch a,sys_organ o,
>         (select (@rownum :=0) ) b
>         where  a.org_id=o.org_id
>         and a.org_id=#{org_id}
>         <!-- 判断是否有查询内容-start -->
>         <if test="search.brchId != null and search.brchId != ''">
>             AND a.brch_id=#{search.brchId}
>         </if>
>         <if test="search.brchName != null and search.brchName != ''">
>             AND a.brch_name LIKE concat(concat('%', #{search.brchName}), '%')
>         </if>
>         <!-- 判断是否有查询内容-end -->
>         <!-- 没有排序条件，自定义默认排序字段 -->
>         <choose>
>             <when test="order != null and order != ''">
>                 ORDER BY ${order}
>             </when>
>             <!-- 默认按照用户创建时间倒序 -->
>             <otherwise>ORDER BY a.brch_name asc</otherwise>
>         </choose>
>         <!-- 分页条件 -->
>         <if test="start!=null and length>=0 ">
>             limit #{start},#{length}
>         </if>
>     </select>
>     
>     <!-- 部门合计行，mysql语法此语句仅作为pdf报表打印测试用，忽略复杂业务逻辑，注意【先聚合计算再格式化】的先后顺序 -->
>     <select id="getBrchSum" parameterType="Map" resultType="Map" databaseId="mysql">
>        select CAST(sum(IFNULL(BRCH_LEVEL,0)) AS DECIMAL(10,2)) AS level_sum from sys_branch;
>     </select>
>     
>     <!-- 部门列表，oracle语法 -->
>     <select id="getBrchList" parameterType="Map" resultType="Map" databaseId="oracle">
>     select * from (
>         select rownum as rn, a.brch_id as id, a.brch_id, a.brch_name,a.img_wrap,a.img,
>         case when a.parent_brch_id = '' then '-'
>         else (select brch_name from sys_branch where brch_id=a.parent_brch_id)
>         end parent_brch_id, a.open_oper_id,a.brch_state,
>         o.img organ_img,
>         to_char(nvl(a.BRCH_LEVEL,0),'fm999990.00') as level
>         from sys_branch a,sys_organ o
>         where  a.org_id=o.org_id
>         and a.org_id=#{org_id}
>         <!-- 判断是否有查询内容-start -->
>         <if test="search.brchId != null and search.brchId != ''">
>             AND a.brch_id=#{search.brchId}
>         </if>
>         <if test="search.brchName != null and search.brchName != ''">
>             AND a.brch_name LIKE concat(concat('%', #{search.brchName}), '%')
>         </if>
>         <!-- 判断是否有查询内容-end -->
>         <!-- 没有排序条件，自定义默认排序字段 -->
>         <choose>
>             <when test="order != null and order != ''">
>                 ORDER BY ${order}
>             </when>
>             <!-- 默认按照用户创建时间倒序 -->
>             <otherwise>ORDER BY a.brch_name asc</otherwise>
>         </choose>
>       )
>       <!-- 分页条件 -->
>             where rn &lt;= (#{start} + #{length}) and rn &gt; #{start}
>     </select>
>     <!-- 部门合计行，oracle语法 -->
>     <select id="getBrchSum" parameterType="Map" resultType="Map" databaseId="oracle">
>        select to_char(sum(nvl(BRCH_LEVEL,0)),'fm999990.00') AS level_sum from sys_branch
>     </select>
> ```
***注意：** 【2.6】版本后加入功能，可以将需要打印的报表数据记录在sys_report表中，可以根据actionNo流水号随时取出要打印的内容，相关代码如下：

>其他前台代码与上面的类似，主要是后端代码有所变动：(详情看table_demo示例页打印功能)
>1.ctrl层：
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
>         // ②并将参数放入缓存中，供报表使用，
>         //    其中第三个入参是用于jasper打印，需要额外增加的入参，实际就是一个map的key
>         //    可以是任意不重复的值（需要pdf打印的功能不能重复），一般就用当前url比较好理解
>         resultData = getPageMap(request,resultData,"/sys/auth/brch/query");
>         //获取部门列表        
>         List<Map> brchList = brchServ.getBrchList(resultData);
>         // 获取总记录数
>         Long recordsTotal = brchServ.getBrchCount(resultData);
>        //模拟将数据插入sys_report表打印备份
>         SysActionLogCust actionLog = baseServ.setActionLog(request, Tr_Code.QUERY_LOTTERY);
>         JSONObject json=new JSONObject();
>         json.put("actionNo", actionLog.getActionNo());
>         json.put("data", brchList);
>         baseServ.saveSysReport(actionLog, json, "/ftl/table_demo.ftl", Sys_Code.REPORT_HTML, ?>1L, "/demo/tag/tagExample");
        
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
>         //model.addAttribute("format", "pdf"); // 若不设置此属性，则默认pdf,报表格式,html,xls,pdf，pdf效果最好
>         
>         //③数据源，先查询条件，可从缓存中获取，也可重新赋值
>         //入参即为对应在的查询功能缓存的查询条件的map的key，其key值与queryBrchInfo方法中指定key为同一个
>         Map reportMap=super.getTableSearchData("/sys/auth/brch/query");
        //模拟一个已知的actionNo
>         JSONObject content=baseServ.getSysReportContent("4cf55d6f-3bae-47bc-a4db-28cf2db853ea");
>        List<Map> dataList=(List<Map>)content.get("data");
>         model.addAttribute("jrMainDataSource", dataList);

>         //④取合计行，可举一反三，可计算多个合计数
>         List<Map> list=brchServ.getBrchSum(reportMap);
>         Map map=list.get(0);
>         
>         //⑤组装参数
>         reportMap.put("p_TotAmt", map.get("level_sum"));//金额合计行，从上面的查询结果中获取（举例）
>         reportMap.put("p_Title", "我是网点报表");
>         reportMap.put("p_Auditor",super.getOperId());
>         reportMap.put("p_Creator",super.getOperId());//从session中取当前操作员
>         model.addAllAttributes(reportMap); // 其它参数
>
>         //⑥返回视图页
>         return "reportView"; // 对应jasper-views.xml中的bean id
>     }

> ```


