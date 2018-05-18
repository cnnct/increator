# time\_line标签

#### time\_line**标签的属性 :**

> time\_line标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id：** id属性  
> > **size：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12  
> > \***url：** 后台url  
> > **group\_name：**每组顶部的旗帜。group\_name：文字，flag\_color：背景颜色，同button  
> > **first\_field：**第一个字段，是一个类似合并行的div。name--字段名，type--字段显示类型：图片、超链接、文本，color--颜色，同button，size\_type--大小类型：大、中、小，bold--是否加粗，icon--图标，同button，i\_color--图标颜色，同button。  
> > **btn：**右上角的操作按钮，同table中的cust\_btn，只是没有转义和切换显示隐藏功能。  
> > \***rows：**每行的字段属性：name--字段名，type--字段显示类型：超链接、文本，color--颜色，同button，size\_type--大小类型：大、中、小，bold--是否加粗，icon--图标，同button，i\_color--图标颜色，同button。

#### time\_line标签的引入方式 :

```
<@time_line id="demo_time_line" size="12" url="${base}/demo/tag/timeLine"
    group_name={'group_name':'groupName','flag_color':'flagColor'} group_image="groupImage"
    panel={
        row_icon : {'icon':'icon','i_color':'iColor'},
        row_label : "rowLabel",
        head_have : "headHave",
        head : "head",
        sub_head : "subHead",
        panel_collapse : "panelCollapse",
        right_top_icon : {'right_top_icon':'rightTopIcon','right_top_i_color':'rightTopIColor'},
        right_top_info : "rightTopInfo",
        row_id : "rowId",
        rows : [
          [
            {'name':'field2','type':'a','color':'success','size_type':'large','bold':'true'},
            {'name':'field3','type':'text','color':'danger','size_type':'middle','bold':'true'},
            {'name':'field4','type':'text','color':'danger','size_type':'middle','bold':'true'},
            {'name':'field5','type':'a','color':'success','size_type':'small','bold':'true'}
          ],
          [
            {'name':'field6','type':'a','color':'success','size_type':'large','bold':'true','icon':'saved','i_color':'info'},
            {'name':'field7','type':'text','color':'danger','size_type':'middle','bold':'true','icon':'saved','i_color':'success'},
            {'name':'field8','type':'text','color':'danger','size_type':'middle','bold':'true','icon':'saved','i_color':'warn'},
            {'name':'field9','type':'a','color':'success','size_type':'small','bold':'true','icon':'saved','i_color':'danger'}
          ]
        ],
        btn : [
         {
          "name":"test1",
          "onclick":"doTest(this)",
          "text":"自定义",
          "icon":"ext_assessedbadge",
          "color":"success",
          "auth_key":"brch_cust",
          "title":"提示"
          }
       ]
    } 
/>
```

```
如果需要修改内容，调用如下方法：
timeLineQuery('demo_time_line', 'queryForm');
每一块中都可存放一个值在一个隐藏input中，可点击按钮取值：
<#--获取id-->
function doTest(obj) {
    console.log($(obj).parent().find('input').val());
}
</script>
```

#### time\_line标签显示效果图 :



