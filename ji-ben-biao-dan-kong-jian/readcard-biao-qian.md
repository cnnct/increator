# read\_card标签

#### 代码示例

```
<@init_page title="部门管理">
    <#-- 读卡控件 -->
    <@read_card />
    <#-- ===================== 查询栏 ===================== -->
    <@query_bar id="queryForm">
        <@form_group class="row">
              <@button  value="读卡" onclick="readcard()" icon="credit-card"  />
        </@form_group>
    </@query_bar>
</@init_page>
<script>
    <#-- 读卡 -->
    function readcard() {
        //getCardInfo方法位于/ocx/readcard/read_card.js中
        getCardInfo("cardNo");
    }
</script>
```

#### 相关配置：

> /config/parameter/para.properties
>
> ```
> #读卡控件相关配置
> readcard_ocx_codebase=ICCInterActiveXT.CAB
> readcard_ocx_version=1.0.0.1
> readcard_ocx_clsid=00A78B01-6080-4769-AD98-4D66A35B2D0E
> ```

#### 效果示例图：

![](/assets/readcard1.png)

#### 



