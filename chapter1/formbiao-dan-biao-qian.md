# **Form标签**

#### **form标签的属性：**

> form标签有5个属性分别为id、class、name、action,enctype**其中id属性为必填项**；  
> >**id \* ：** id属性
>>
> > **name ：** name属性
> >
> > **class：** class属性
> >
> > **action：** action属性
> >
> > **enctype:** enctype属性，enctype="multipart/form-data"，用于文件上传

#### form标签的引入方式如下：

```html
    <@form id="demoform" name="demoform" action="userLogin.do" >
             <@form_group class="row">
                     <@input label="姓名：;true" id="name" name="name1"  type="text" size="3"  />
                     <@input label="邮箱：;true" id="email1" name="email"  type="email" size="3" />
                     <@input label="邮编：;true" id="name1" name="name"  type="text" size="3"  />
              </@form_group>
              <@form_group class="row form-group-select">
                     <@select label="选择框1：;true" id="jskd" sql_key="syscode1"  name="sle" show_field="CODE_NAME" value_field="CODE_VALUE" default_val="2" choice_have="true" size="3"/>
                     <@code_select label="选择框2：;true" id="select-11" name="sle" code_type="AREA_TYPE" default_val="2"  no_show="1"  size="3" choice_have="true" select_more="" />
                     <@code_select label="选择框3：;true" id="select-111" name="sle" code_type="AREA_TYPE" default_val="2"  no_show="1"  size="3" choice_have="true" select_more="" />        
              </@form_group>
              <@form_group class="row">
                     <@input_tree  label="input树1：;false" size="3" id="but6" tree_id="tree6" name="valuetree6" sql_key="sysfunc7" checkbox_have="true"/>
                     <@input_tree  label="input树2：;false" size="3" id="but7" tree_id="tree7" name="valuetree7" sql_key="sysfunc7" checkbox_have="true"/>
                     <@input_tree  label="input树3：;false" size="3" id="but5" tree_id="tree5" name="valuetree5" sql_key="sysfunc7" checkbox_have="true"/>
              </@form_group>
              <@form_group class="row">
                     <@date_time  label="时间框1：;false" id="date1" name="start_time3" size="3"/>
                     <@date_time  label="时间框2：;false" id="date2" name="start_time4" size="3"/>
                     <@date_time  label="时间框3：;false" id="date3" name="start_time5" size="3"/>
               </@form_group>
              <@form_group class="row">
                     <@search_input  label="search框1：;false" id="search1" name="searchOrgName" sql_key="org_name1" show_item="item.org_id + ' _ ' + item.org_name" show_value="org_name" hidden_value="org_id" size="3"/>
                     <@search_input   label="search框2：;false" id="search2" name="searchOrgName" sql_key="org_name1" show_item="item.org_id + ' _ ' + item.org_name" show_value="org_name" hidden_value="org_id" size="3"/>
                     <@search_input   label="search框3：;false" id="search3" name="searchOrgName" sql_key="org_name1" show_item="item.org_id + ' _ ' + item.org_name" show_value="org_name" hidden_value="org_id" size="3"/>
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
                     <@button id="submit" type="submit"   value="提交" icon="search"/>
                    <@button id="repeat3" type="button"   value="重置" icon="repeat"/>
             </@form_group>
        </@form>
```

#### ![](/assets/form.png)form表单的验证引入方式：

![](/assets/validate1.png)

![](/assets/validate2.png)

自定义表单正则表达式验证，文件名为custom\_validate.js



![](/assets/validate3.png)
####form表单的验证引入方式：
![](/assets/validate5.png)


