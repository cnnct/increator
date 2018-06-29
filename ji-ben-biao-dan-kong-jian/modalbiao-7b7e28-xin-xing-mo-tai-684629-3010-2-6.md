# modal**标签**

#### 注：此新型模态框意在替换modal\_iframe，推荐使用此标签。

#### modal**标签的属性 :**

> **其中必填项加上了\*号，如下所示 :**
>
> > \***id：**id属性
> >
> > **modal\_title：**标题
> >
> > **drag：**是否可拖动，默认不可拖动
> >
> > **class：**样式\(不填：中等模态框;modal-lg：大模态框;modal-sm：小模态框\)
> >
> > **is\_full\_screen：**为打开时是否全屏的属性，默认“false”,可填值"true","false"
> >
> > **foot\_content\_position【2.3】：**模态框脚中内容的位置\(默认right\)：left\(左\)、right\(右\)、center\(居中\)，如果为center，那么模态框脚中标签的一些属性可能会失效，比如button的size、position。

#### modal标签的引入方式 :

```
主页面引入：
<#-- ===================== 修改框 ===================== -->
<@modal class="modal-lg" id="modal_edit" modal_title="修改">
    <@button id="edit_btn" icon="saved" value="提交" onclick="save()" check_resubmit="true"/>
    <@button id="repeat" type="button" value="清空" icon="repeat" onclick="formReset('edit_form')"/>
</@modal>
（注：如果模态框的脚部没有内容，可以不写，如详情页：）
<#-- ===================== 详情框 ===================== -->
<@modal id="modal_view" modal_title="详情" class="modal-lg"/>
主页面按钮：
<@button value="批量激活" onclick="activeAndCancel('active')" icon="ok-sign" auth_key="roleActive"/>
主页面js部分：
<script>
    <#-- 修改 -->
    function toEdit(obj,tableId) {
        //获取列id
        var id=getFirstInputId(obj);
        var row=getTableRowById(id,tableId);
        var codeName=getCodeName("1","STATE",tableId);
        if(row.del_flag==codeName){
            alert("已经注销的不能修改");
            return;
        }else{
            $("#modal_edit").modal({remote:"${base}/sys/auth/role/toEdit/" + id});
        }
    }
</script>

编辑子页面：
<@form id="edit_form">
    <@input id="edit_roleId" name="roleId" type="hidden" value="${cust.roleId}"/>
    <@form_group class="row">
        <@input label="名称,true,2" name="roleDesc" type="text" size="4" value="${cust.roleDesc}" id="edit_roleDesc"/>
        <@code_select label="机构,true,2" id="edit_orgId" name="orgId" code_type="ORG_ID" default_val="${cust.orgId}" size="4" choice_have="true"/>
    </@form_group>
    <@form_group class="row">
        <@input_tree label="权限,,2" size="10" id="edit_funcId" tree_id="edit_treeId" name="funcName" sql_key="sysfunc10" 
            checkbox_have="true" sql_condition="${cust.roleId}"/>
    </@form_group>
    <@form_group class="row">
        <@text_area label="备注信息,false,2" id="edit_remarks" name="remarks" value="${cust.remarks}"  size="10"/>
    </@form_group>
</@form>
<script>
    <#-- 保存 -->
    function save() {
        //表单验证
        if (!$("#edit_form").valid()) {
            return;
        }
        //提交表单
        postform({
            "tableId":"mytable",
            "url":"${base}/sys/auth/role/save/edit",
            "formId":"edit_form",
            "modalId":"modal_edit"
        });
    }
    <#-- 表单验证 -->
    $("#edit_form").formValidate({
        rules: {
            "roleDesc": {
                required: true,
                maxlength: 64,
                remote:{
                    url:"${base}/sys/auth/role/verify",
                    type:'post',
                    async: false,
                    data:{
                        roleDesc:function(){
                            return $("#edit_roleDesc").val();
                        },
                        roleId:function(){
                            return $("#edit_roleId").val();
                        }
                    }
                }
            },
            "orgId": {
                required: true,
                maxlength: 20
            },
            "remarks": {
                maxlength: 255
            }
        },
        messages:{
            "roleDesc": {
                    remote:"该用户名已经存在"
               }
        }
    })
</script>
```

#### modal标签显示效果图 :

![](/assets/modal.png)

