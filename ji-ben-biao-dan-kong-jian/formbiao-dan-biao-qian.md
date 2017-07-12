# **Form标签**

#### **form标签的属性 :**

> form标签有5个属性分别为id、class、name、action,enctype**其中id属性为必填项**；
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **class：** class属性
> >
> > **action：** action属性
> >
> > **enctype:** enctype属性，enctype="multipart/form-data"，用于文件上传

#### form标签的引入方式如下 :

```html
    <@form id="demoform" name="demoform" action="userLogin.do" >
         <@form_group class="row">
                <@input label="邮编：;true" id="name" name="name"  type="text" size="5"  />
               <@input label="邮件：;true" id="email" name="email"  type="email" size="5" />
         </@form_group>
         <@form_group class="row">
                  <@input label="密码：;true" id="inputPassword" name="pwd"  type="password" size="5" />
               <@input label="再次输入：;true" id="inputPasswordRepeat" name="pwd1"  type="password" size="5" />
         </@form_group >
         <@form_group class="row form-group-select">
               <@select label="选择框1：;true" id="hjfdh" sql_key="syscode1"  name="sle" show_field="CODE_NAME" value_field="CODE_VALUE"   size="5" select_more="true"/>
               <@code_select label="选择框2：;true" id="select-11" name="sle1" code_type="AREA_TYPE" default_val="2"  no_show="1"  size="5" choice_have="true" select_more="" />    
         </@form_group>
         <@form_group class="row">
                <@cas_select_parent  label="级联1：;false" id="parent" name="name1" sql_key="sysfunc1" show_field="TITLE" value_field="FUNC_ID"  size="5" child_info="child;sysfunc3;TITLE;FUNC_ID" default_val="01"/>
               <@cas_select_child  label="级联2：;false" id="child"   name="name1" size="5"  child_info="grandson;sysfunc5;TITLE;FUNC_ID" sql_key="sysfunc2" show_field="TITLE" value_field="FUNC_ID" default_val="0106" sql_condition="01"/>
         </@form_group>
          <@form_group class="row">
               <@cas_select_child  label="级联3：;false" id="grandson"  name="name1" size="5" child_info="padson;sysfunc6;TITLE;FUNC_ID"/>
               <@cas_select_child  label="级联4：;false" id="padson"  name="name1" size="5"/>
           </@form_group>
         <@form_group class="row">
                <@input_tree label="input树1：;false" size="5" id="but3" tree_id="tree3" name="valuetree3" sql_key="sysfunc7" checkbox_have="true"/>
                <@input_tree label="input树2：;false" size="5" id="but4" tree_id="tree4" name="valuetree4" sql_key="sysfunc7" checkbox_have="false"/>
         </@form_group>
         <@form_group class="row">
                <@date_time label="时间框1：;false" id="date1" name="start_time1" size="5"/>
                <@search_input  label="search框1：;false" id="search1" name="searchOrgName" sql_key="org_name1" show_item="item.org_id + ' _ ' + item.org_name" show_value="org_name" hidden_value="org_id" size="5"/>
          </@form_group>
         <@form_group class="row">
                <@search_input  label="search框2：;false" id="search2" name="searchOrgName" sql_key="org_name1" show_item="item.org_id + ' _ ' + item.org_name" show_value="org_name" hidden_value="org_id" size="5"/>
                <@date_time  label="时间框2：;false" id="date2" name="start_time2" size="5"/>
          </@form_group>
         <@form_group class="row">
               <@text_area label="文本域1：;false" id="username1" name="ntextame" value="name"  size="5" /> 
          </@form_group>
         <@form_group class="row">
                <@code_radio name="code_type2" code_type="AREA_TYPE" default_val="28" readonly="true"/>
         </@form_group>
         <@form_group class="row">
                <@code_checkbox name="code_type1" code_type="AREA_TYPE" default_val="09,28,58" readonly="true" />
         </@form_group>
         <@form_group >
                <@button id="submit" type="submit"    value="提交" icon="search"/>
               <@button id="repeat3" type="button"    value="重置" icon="repeat"/>
        </@form_group>
 </@form>
```

#### ![](/assets/form1.png)form表单的引入方式 :

![](/assets/validate1.png)

#### form表单显示结果 :

![](/assets/validate2.png)

自定义表单正则表达式验证，文件名为custom\_validate.js

![](/assets/validate3.png)

#### form表单的验证显示结果 :

![](/assets/validate5.png)
#### form表单清空 :
可以调用让button调用formReset('formId')方法清空指定form表单，或者在button加入class属性值'form-reset',清空当前表单
<@button id="repeat" type="button" value="清空" icon="repeat"  class="form-reset"/>


