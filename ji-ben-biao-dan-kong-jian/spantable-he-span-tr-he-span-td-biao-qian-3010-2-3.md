# span\_table和span\_tr和span\_td**标签**

#### 注：span\_table和span\_tr和span\_td标签为一体的。

#### span\_table**标签的属性 :**

> span\_table标签有2个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：**size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12
> >
> > **label\_color：** 是否启用彩色风格，默认启用

#### span\_tr**标签的属性 :**

> span\_tr标签有1个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12

#### span\_td**标签的属性 :**

> span\_td标签有2个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",当type为label时，默认size为2，当type为value时，默认为10
> >
> > **type ：** 文本类型：分为label和value，默认value

#### step和step\_element标签的引入方式 :

```
    <@step title="步骤表单示例" id="add_step" form_id="add_form" count="3">
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

