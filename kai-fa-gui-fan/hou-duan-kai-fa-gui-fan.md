
#前端页面开发

---

* 所有页面首先引入 **init\_page** 标签，页面内容都放在标签里面
* ```html
  <@init_page title="xxx管理">
 
  </@init_page>
  ```
* 一个简单的页面例子，已操作员管理为例，包括查询栏、按钮栏、表格
* 引入查询栏标签 **query\_bar**
* ```html
  <@query_bar>
    <table>
      <tr>
        <th>编号</th>
        <td><input type="text" name="operId"></td>
      <tr>
      <tr>
        <th>姓名</th>
        <td><input type="text" name="operName"></td>
      </tr>
      <tr>
        <td><button type="button" class="btn btn-default btn-sm" onclick="queryInfo()">查询</button></td>
      </tr>
    </table>
  </@query_bar>
  ```
* 引入按钮栏 **button\_bar**
* ```html
  <@button_bar>
    <@button icon="saved" value="保存" onclick="save()"/>
    <@button icon="remove" value="删除" onclick="del()"/>
  </@button_bar>
  ```
* 引入表格栏 **table** （其他控件参看**基本表单控件**和**扩展表单控件**），表格控件的使用包含在此例中
* ```html
  <@table url="${base}/oper/query"
  thead="编号,姓名,机构,部门,状态,级别"
  fields="id,oper_id,oper_name,org_name,brch_name,oper_state,oper_level"/>
  <!-- 所有提交的url地址的前缀都要加上 ${base} -->
  <!-- 表格控件目前需三个参数：-->
  <!-- url： 提交的后台地址 thead： 表头显示的字段名（不包括第一列的id列） fields：sql语句中显示的字段名 -->
  <!-- 首字段 id 固定，mapper 中提供的 sql 语句必须提供 id 字段名（详细见后续 mapper 语句编写）-->
  ```
* 表格数据显示例子如下图：
![](/assets/20170623101159.jpg)
* 表格相关js方法
* 查询方法
* ```js
  function queryInfo() {
  //提交查询栏query_bar的数据，直接调用postform()，不需要参数
  //后台提供对应的实体类或相同名字的参数自动封装
  postform();
  }
  ```
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
  $("#modal_view_iframe").attr("src", "${base}/oper/view?operId=" + id);
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
  $("#modal_edit_iframe").attr("src", "${base}/oper/edit?operId=" + id);
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
         alert({message: "删除成功", title: "提示"});
         }
       }
     })
  }
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
* getSelectId() 获取选中的表格行的id值，多个以逗号隔开
* getSelectIndex() 获取选中的记录数

# 后端程序开发

---
- Controller 的编写
- 类需继承 BaseCtrl 类
- ```java
 public class OperCtrl extends BaseCtrl {}
```
- 模块首页
- ```java
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
- 获取表格数据
- ```java
 /**
 * 获取操作员信息
 * @param request 参数固定为 HttpServletRequest
 */
 @RequestMapping("/query")
 @ResponseBody //必须以json格式返回，此注释必须加
 public ResultData queryOperInfo(HttpServletRequest request) {
 ResultData resultData = new ResultData(Result_Code.SUCCESS);
 try {
 //分页参数
 resultData = getPageMap(request);
 //sql条件（用于sql语句中where的筛选条件，若有，则如下写法）
 resultData.put("org_id", getOper().getOrgId());
 //获取操作员列表，返回必须是List<Map>格式
 List<Map> operList = operServ.getOperList(resultData);
 //获取总记录数
 Long recordsTotal = operServ.getRecordCount(resultData);
 //返回数据至页面
 resultData = initPagination(operList, recordsTotal);
 } catch (Exception e) {
 resultData.setResultData(e);
 log.error(e.getMessage());
 e.printStackTrace();
 }
 return resultData;
 }
```

# Mapper编写

---


