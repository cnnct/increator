# 浏览器session切换问题

* #### 问题描述

由于某些操作员在浏览器窗口一个TAB选项卡上登录一个用户，在另一个TAB选项卡上登录另一个用户，以为可以同时登录多个用户操作，其实不然，第一个登录的用户会被第二个挤掉，但第一个页面不刷新看不出来，会误导操作员。

* #### **解决方案**

**button标签会自动验证当前页面显示用户是否与后台一致，所以强烈建议提交表单等操作使用button标签。**

**如果不使用button标签，在提交表单等操作前，须调用JS函数validateUser\(\)进行验证，以免误导用户。**

在ajax调用后台之前验证即可，最好在JS方法第一行调用。

调用JS函数validateUser\(\)进行验证示例：

```
<#-- 保存操作员信息 -->
function save() {

    //比如在此处调用验证
    validateUser();

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
```



