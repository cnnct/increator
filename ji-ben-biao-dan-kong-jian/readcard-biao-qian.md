# read\_card标签

```
<@init_page title="部门管理">
    <#-- 读卡控件 -->
    <@read_card />
    <#-- ===================== 查询栏 ===================== -->
    <@query_bar id="queryForm">
        <@form_group class="row">
              <@button  value="查询" onclick="queryInfo()" auth_key="brch_query"/>
        </@form_group>
    </@query_bar>
</@init_page>
```

例子：

![](/assets/readcard1.png)

