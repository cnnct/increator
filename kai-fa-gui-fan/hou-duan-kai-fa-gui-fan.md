# 前端页面开发

---

* 所有页面首先引入**init\_page**标签，页面内容都放在标签里面

```
    <@init_page title="xxx管理">

    </@init_page>
```

* 一个简单的页面例子，已操作员管理为例，包括查询栏、按钮栏、表格

* 引入查询栏标签 **query\_bar**

```
     <@query_bar>
        <@form_group class="row">
            <@input label="编号" name="operId"  size="2"  />
            <@input label="姓名" name="operName"  size="2"  />
            <@button  value="查询" onclick="queryInfo()"/>
        </@form_group>
    </@query_bar>
```

* 引入表格栏 **table** （其他控件参看**基本表单控件**和**扩展表单控件**），表格控件的使用包含在此例中，**详细使用参照table标签**
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
                    cust_btn=[{"name":"test1","onclick":"doTest('sd')","text":"自定义","icon":"saved","color":"success","auth_key":"brch_cust"}]
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
  8. btn：显示的按钮，目前有6个固定的常用按钮：
     detail 查看详情，edit 修改，delete 删除，active 激活，cancel 注销，显示按钮必须开启操作栏
     每个按钮有三个属性，name属性只有以上六种值，auth_key为权限属性，匹配sys_func表中的url，cust_label属性为自定义按钮的名字，存在默认名
  9. cust_btn:cust_btn属性是除了以上常用按钮的自定义按钮,五项属性中name属性和onclick属性为必填项，且onclick的值现在只支持
      "doTest('sd')"这种传参方式，不支持'doTest("sd")'方式，text属性为button的显示值，icon属性为图标，默认为搜索图标，
      color属性为颜色属性，可以填写的值为"success"、"danger"、"info"、"warning"、"primary"，默认为蓝色,auth_key为权限属性，匹配sys_func表中的url

  10. sort：支持排序功能的字段，默认除了id列和操作列外所有字段都支持
  11.img_fields:支持缩略图功能，img_fields={"img_wrap":"img"},"img_wrap"为缩略图字段，"img"为原图字段,点击缩略图弹出原图
  12. 表格若不需要id列，fields 中去掉 id 字段，同时后台 sql 也去掉 id 字段：如下
      fields="oper_id,oper_name,org_name,brch_name,oper_state,oper_level"
  备注：存在id列的情况下，首字段 id 固定，mapper 中提供的 sql 语句必须提供 id 字段名（详细见后续 mapper 语句编写）
  -->
  ```
* 表格数据显示例子如下图：
  ![](/assets/table.png)
* 表格相关js方法
* 查询方法
* ```js
    function queryInfo() {
        //提交查询栏query_bar的数据，直接调用postform()，不需要参数
        //后台提供对应的实体类或相同名字的参数自动封装
        postform();
    }
  ```
* 表格操作栏的方法 按钮名\_item\(id\)
* 表格操作栏的 '详情' 方法
* ```js
    /**
     * 查看详情（js方法名固定写法）
     * 方法名中的 id 为表格第一列的 id 值
     */
    function viewDetail(id) {
        /**
         * 详情框和编辑框等需要从后台读取数据回显的情况，一般弹框用 iframe 弹框
         * 此处 modal_view_iframe 固定写法
         */
        $("#modal_view_iframe").attr("src", "${base}/oper/view/" + id);
    }
  ```
* 表格操作栏的 '修改' 方法
* ```js
    /**
     * 修改操作员信息（js方法名固定写法）
     * 方法名中的 id 为表格第一列的 id 值
     */
    function editItem(id) {
        /**
         * 详情框和编辑框等需要从后台读取数据回显的情况，一般弹框用 iframe 弹框
         * 此处指定iframe的src属性，传递的数据暂时使用url后面跟参数的get方式
         * 此处 modal_edit_iframe 固定写法
         */
        $("#modal_edit_iframe").attr("src", "${base}/oper/edit/" + id);
    }
  ```
* 表格操作栏的 '删除' 方法
* ```js
    /**
     * 删除操作信息（js方法名固定写法）
     */
    function delItem(id) {
        confirm({
            message: "确定删除？",
            callback: function(result) {
                if (result) {
                    //ajax直接提交方法 directpost(url, data) data为json对象
                    directpost("${base}/oper/del", {"operId": id});

                }
            }
        })
    }
  ```
* 表格操作栏的 '激活' 方法
* ```js
    <#-- 激活操作员（操作栏内）（js方法名固定写法） -->
    function activeItem(id) {
        //判断是否执行该操作
        confirm({
            message: "是否执行操作？",
            callback: function(result) {
                if (result) {
                    //ajax直接提交方法 directpost(url, data) data为json对象
                    directpost("${base}/oper/activeAndCancel", {"ids": id, "flag": "active"});
                }
            }
        })
    }
  ```
* 表格操作栏的 '注销' 方法
* ```js
    <#-- 注销操作员（操作栏内）（js方法名固定写法） -->
    function cancelItem(id) {
        //判断是否执行该操作
        confirm({
            message: "是否执行操作？",
            callback: function(result) {
                if (result) {
                    //ajax直接提交方法 directpost(url, data) data为json对象
                    directpost("${base}/oper/activeAndCancel", {"ids": id, "flag": "cancel"});
                }
            }
        })
    }
  ```
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
* 新增数据时的提交方法

* 表单写法举例（此处以操作员为例）

* ```html
    <@modal_body class="modal-lg" id="modal_add" modal_title="添加操作员">
        <@form id="add_form">
            <@form_group class="row">
                <@input label="编号：;true;2" name="oper.operId" type="text" size="2"/>
                <@input label="姓名：;true;2" name="oper.operName" type="text" size="2"/>
                <@code_select id="add_sex" label="性别：;false;2" name="oper.sex" code_type="SEX" choice_have="true" size="2"/>
            </@form_group>
            <@form_group class="row">
                <@input label="身份证号：;false;2" name="oper.certNo" type="text" size="2"/>
                <@input label="手机号：;false;2" name="oper.teleNo" type="text" size="2"/>
                <@code_select id="add_operlevel" label="用户级别：;true;2" name="oper.operLevel" code_type="OPER_LEVEL" choice_have="true" size="2"/>
            </@form_group>
            <@form_group class="row">
                <@input_tree label="部门；;true;2" name="oper.brchId" size="2" id="brch_id" tree_id="brch_tree" sql_key="sysbrch1" checkbox_have="false"/>
                <@input label="密码：;true;2" name="oper.pwd" type="password" size="2"/>
            </@form_group>
            <@form_group class="row">
                <@label name="角色：" must_star="true" size="2"/>
                <@dual_select_list id="add_roleId" name="role.roleId" show_field="role_desc" value_field="role_id" sql_key="sysoperrole1" sql_condition="'';''" size="6"/>
            </@form_group>
        </@form>
    </@modal_body>
    <@modal_foot>
        <@button icon="saved" value="提交" onclick="save()"/>
    </@modal_foot>
  ```
* 提交方法举例
* ```js
    /**
     * 新增数据时（此例为新增操作员信息），一般使用普通模态框弹窗（非 iframe）
     * 弹窗等具体控件用法参看 '基本表单控件' 和 '扩展表单控件'
     */
    <#-- 保存操作员信息 -->
    function save() {
        //提交表单
        /**
         * ajax表单提交方法 postform(url, form_name, convert_name)
         * url： 提交地址
         * form_name： 表单id，可为空
         * convert_name： 需转换的name属性，可为空，例子："role1.id,role2.id ..."
         * 当vo类中的成员变量为List类型时就需要转换，否则后台vo类不能自动封装
         * 关于po类，cust类和vo类的说明和使用场景参看ssm框架相关知识
         */
        postform("${base}/oper/save", "add_form", "role.roleId");
        //提示
        alert({message: "保存成功", title: "提示"});
    }
  ```
* 其他常用js方法
* getSelectId\(\) 获取选中的表格行的id值，多个以逗号隔开
* getSelectIndex\(\) 获取选中的记录数

# 后端程序开发

---

* Controller 的编写
* 类需继承 BaseCtrl 类
* ```java
    public class OperCtrl extends BaseCtrl {}
  ```
* 模块首页
* ```java
    /**
     * 操作员首页
     * @param model
     */
    @RequestMapping("/index")
    public String operIndex(Model model) {
        //统一使用封装后的jsonObject，即ResultData
        ResultData resultData = new ResultData(Result_Code.SUCCESS);
        //跳转的页面路径
        return "/sysmanager/oper/oper_index";
    }
  ```
* 获取表格数据
* ```java
   /**
       * 获取操作员信息
       *
       * @param request
       * @return
       */
      @RequestMapping("/query")
      @ResponseBody
      public ResultData queryOperInfo(HttpServletRequest request)throws Exception  {
          ResultData resultData = new ResultData(Result_Code.SUCCESS);
          //分页参数
          resultData = getPageMap(request);
          //sql条件（用于sql语句中where的筛选条件，若有，则如下写法）
          resultData.put("org_id", getOper().getOrgId());
          //获取操作员列表
          List<Map> operList = operServ.getOperList(resultData);
          //获取总记录数
          Long recordsTotal = operServ.getRecordCount(resultData);
          //返回数据至页面
          initPagination(resultData, operList, recordsTotal);
          return resultData;
      }
  ```
* 实现类（Service层）注意事项
* ```java
    /**
     * 实现类需继承 BaseImpl 基础实现类
     */
    @Repository //dao层注解
    public class OperServImpl implements OperServ {
        /**
         * 获取操作员列表
         * @param pageMap 分页排序map
         */
        @Override
        public List<Map> getOperList(Map pageMap) {
            try {
                List<Map> operList = operMapper.getOperList(pageMap);
                return operList;
            } catch (Exception e) {
                throw new CustomException(e);
            }
        }
    }
  ```

# Mapper编写

---

* 获取表格显示的数据
* ```xml
    <!-- 查找所有操作员信息（分页显示）-->
    <!-- 接受参数 parameterType 必须为 Map类型 -->
    <!-- 返回值 resultType 必须为 Map -->
    <!-- 表格转义功能还未实现，转义功能直接在sql中实现，后续优化 -->
    <select id="getOperList" parameterType="Map" resultType="Map">
        select a.oper_id as id, a.oper_id, a.oper_name, b.org_name, c.brch_name, a.oper_state, a.oper_level
        from sys_operator a, sys_organ b, sys_branch c
        where a.org_id=b.org_id
        and a.brch_id=c.brch_id
        and a.org_id=#{org_id}

        <!-- 查询的字段必须以 search.xxx 形式书写 -->
        <!-- 上述查询栏内的编号和姓名 name 属性分别为 operId 和 operName，故此调用如下所示 -->
        <!-- 判断是否有查询内容-start -->
        <if test="search.operId != null and search.operId != ''">
            and a.oper_id=#{search.operId}
        </if>
        <if test="search.operName != null and search.operName != ''">
            and a.oper_name LIKE concat(concat('%', #{search.operName}), '%')
        </if>
        <!-- 判断是否有查询内容-end -->

        <!-- 此处固定写法 -->
        <!-- 没有排序条件，自定义默认排序字段 -->
        <choose>
            <when test="order != null and order != ''">
                order by ${order}
            </when>
            <!-- 默认按照用户创建时间倒序 -->
            <otherwise>order by a.open_date desc</otherwise>
        </choose>

        <!-- 分页条件，记录起始start，获取记录长度length -->
        limit #{start},#{length}
    </select>
  ```
* 获取查询的数据的总数
* ```xml
    <!-- 接受参数 parameterType 必须为 Map类型 -->
    <!-- 返回值 resultType 自定义 -->
    <!-- 查找所有操作员信息（记录数） -->
    <select id="getRecordCount" parameterType="Map" resultType="java.lang.String">
        select count(1)
        from sys_operator a, sys_organ b, sys_branch c
        where a.org_id=b.org_id
        and a.brch_id=c.brch_id
        and a.org_id=#{org_id}
        <!-- 判断是否有查询内容-start -->
        <if test="search.operId != null and search.operId != ''">
            and a.oper_id=#{search.operId}
        </if>
        <if test="search.operName != null and search.operName != ''">
            and a.oper_name LIKE concat(concat('%', #{search.operName}), '%')
        </if>
        <!-- 判断是否有查询内容-end -->
    </select>
  ```



