# init\_page**标签**

#### init\_page**标签的属性 :**

> init\_page标签为初始化加载标签，有3个属性分别为为title、link、script
>
> > **title  ：** title属性
> >
> > **link ：** link 属性为引入css文件的属性
> >
> > **script ：** script属性引入js文件的属性hjhj

#### init\_page标签的引入方式 :

```
 <@init_page title="登录测试页面" link="${base}/assets/css/bootstrap-duallistbox.css;${base}/assets/css/jquery-ui.css;${base}/assets/css/bootstrap-datetimepicker.css" 
  script="${base}/assets/js/ace-extra.js;${base}/assets/js/date-time/bootstrap-datetimepicker.js;${base}/assets/js/date-time/locales/bootstrap-datepicker.zh-CN.js;${base}/assets/js/jquery-ui.js">

  .........

 </@init_page>
```



