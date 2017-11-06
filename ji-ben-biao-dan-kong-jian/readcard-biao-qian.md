# read\_card标签

```
<@init_page title="部门管理">
    <#-- 读卡控件 -->
    <@read_card />
    <#-- ===================== 查询栏 ===================== -->
    <@query_bar id="queryForm">
        <@form_group class="row">
            <@input label="部门编号" name="brchId"  size="2"  />
            <@input label="部门名称" name="brchName"  size="2"  />
              <@button  value="查询" onclick="queryInfo()" auth_key="brch_query"/>
        </@form_group>
    </@query_bar>    
</@init_page>
```

例子：

![](/assets/readcard.png)

