# block\_table标签

### 注：不兼容IE8及以下版本浏览器。

#### block\_table**标签的属性 :**

> block\_table标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id：** id属性  
> > **size：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为12  
> > \***url：** 后台url（后台代码参考示例）  
> > **col：**总并排列数  
> > **first\_field：**第一个字段，是一个类似合并行的div。name--字段名，type--字段显示类型：img\(图片\)、a\(超链接\)、text\(文本\)，color--颜色，同button，，除了warning（a为warn，text为warning），size\_type--大小类型：large\(大\)、middle\(中\)、small\(小\)，bold--是否加粗：true\(是\)、false\(否\)，icon--图标，同button，i\_color--图标颜色，同button，除了warning（这里为warn）。注：此处颜色指定的是一整列，还可以单独指定某个值的颜色，key为name拼上ValColor，如：ageValColor（name为age），类型为img时不可用。  
> > **btn：**右上角的操作按钮，同table中的cust\_btn，只是没有转义和切换显示隐藏功能，【2.6】版本后加入title（提示属性），dynswitch动态切换按钮（参考table标签），  
> > \***rows：**每行的字段属性：name--字段名，type--字段显示类型：a\(超链接\)、text\(文本\)，color--颜色，同button，除了warning（a为warn，text为warning），size\_type--大小类型：large\(大\)、middle\(中\)、small\(小\)，bold--是否加粗：true\(是\)、false\(否\)，icon--图标，同button，i\_color--图标颜色，同button，除了warning（这里为warn）。注：此处颜色指定的是一整列，还可以单独指定某个值的颜色，key为name拼上ValColor，如：ageValColor（name为age）。  
> > **\*row\_id：**指定每列的id项  
> > **load\_data\_init:【2.6】** load\_data\_init属性为是否初始化加载数据开关属性，默认为true（首次进页面加载数据）,【1.4】版本后，支持传入的值为“true”，“false”，或指定查询条件的formId，当值为“true”或不填该属性时，默认不带查询条件初始化加载数据，为“false”时不加载数据，为formId时，会带查询条件加载数据,如load\_data\_init="queryForm"  
> > **refresh\_table\_after\_func:【2.6】** refresh\_table\_after\_func 属性用于表格刷新后调用的方法，需要指定方法名，该方法只有一个对象参数，如refresh\_table\_after\_func="doTest1"，详细见示例demo  
> > **auth\_key【2.7】:** 权限属性，如auth\_key="brch\_add",非必填项，如果没有该属性，则为非权限按钮，如果存在，

#### block\_table标签的引入方式 :

```
<@block_table id="demo_act_list" url="${base}/demo/tag/actList" col="2" first_field={'name':'field1','type':'img'}
    rows=[
           [
             {'name':'field2','type':'a','color':'success','size_type':'large','bold':'true'},
             {'name':'field3','type':'text','color':'danger','size_type':'middle','bold':'true'},
             {'name':'field4','type':'text','color':'danger','size_type':'middle','bold':'true'},
             {'name':'field5','type':'a','color':'success','size_type':'small','bold':'true'}
           ],
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
         ]
    btn=[
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
/>
```

```
如果需要修改内容，调用如下方法：
actListQuery(blockTableId);
或传一个表单id，自动将表单中的参数提交到后台
actListQuery(blockTableId, formId);
每一块中都可存放一个值在一个隐藏input中，可点击按钮取值：
<#--获取id-->
function doTest(obj) {
    console.log($(obj).parent().find('input').val());
}
</script>
```

#### block\_table标签显示效果图 :

![](/assets/block_table.png)

