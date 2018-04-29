# step和step\_element**标签**

#### 注：step和step\_element标签为一体的。

#### step**标签的属性 :**

> step标签有4个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> > **title ：** 标题
> > **form\_id：** 表单id属性
> > **has\_button：** 是否有按钮，默认有
> > \***step\_info：** json数组，label为圆形图标下的文字，active表示是否激活，见如下示例。

#### step\_element**标签的属性 :**

> step\_element标签有1个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***step ：** 此为第几步

#### step和step\_element标签的引入方式 :

```
    <@step id="add_step" title="步骤表单示例" form_id="add_form" has_button="true" step_info=[{"label":"标题1","active":"true"},{"label":"标题2"},{"label":"标题3"}]>
        <@step_element step="1">
            <@input label="名称,true,2" name="roleDesc" type="text" size="4" />
        </@step_element>
        <@step_element step="2">
            <@code_select label="机构,true,2" id="orgId"  name="orgId" code_type="org_id" size="4" choice_have="true" />
        </@step_element>
        <@step_element step="3">
            <@text_area label="备注信息,false,2" id="remarks" name="remarks" size="10" />
        </@step_element>
    </@step>
```

```
// 点击上一步、下一步、完成时
$(function() {
    $('#add_step').ace_wizard()
    .on('actionclicked.fu.wizard' , function(e, info){ // 点击上一步和下一步时
        if (info.step == 2) {
            if ("previous" == info.direction) {
                //上一步
            }
            if ("next" == info.direction) {
                //下一步
            }
        }
    })
    .on('finished.fu.wizard', function(e) { // 点击完成时
        //dosomthing...接交表单等
    });
})
```

#### step和step\_element标签显示效果图 :

![](/assets/step.png)

