```
第一步，使用ireport工具绘制报表
```

> ireport使用说明详见“[ireport使用说明](/kuang-jia-she-zhi/bao-biao-he-da-yin/ireportzheng-he-kai-fa-pdf-bao-biao/ireportshi-yong-shuo-ming.md)”，绘制完成的报表文件后缀名为jrxml，并同步编译成二进制报表文件，后缀名为jasper，两个文件一并拷贝到web目录中的reportfiles中，文件命名规则同普通页面命名相同，英文小写+下划线组合，能根据文件名就能看出是什么报表。

# 第二步，代码实现

以下以网点报表为例

* #### 页面代码实现

> 根据业务需要增加打印按钮，注意按钮图标使用：icon="print"
>
> 增加报表页的iframe，注意属性：report\_window="true"
>
> 增加弹出报表页的脚本，同其它打开窗口页脚本类似
>
> ```
> <@table_toolbar name="查询结果" size="8" >
>     <@button  value="新增" data_target="modal_add" icon="plus"/>
>     <@button  value="批量激活" onclick="activeAndCancel('active','mytable')" icon="ok-sign"/>
>     <@button  value="批量注销" onclick="activeAndCancel('cancel','mytable')" icon="remove-sign"/>
>     <@button  value="打印" onclick="showReport()" icon="print"/>
> </@table_toolbar>
>
> <!-- ===================== 打印框 ===================== -->
> <@modal_iframe id="modal_print" report_window="true" modal_title="打印" class="modal-lg"/>
>
> <#-- 报表打印 -->
> function showReport() {
>     $("#modal_print").modalShow("/sys/auth/brch/showReport");
> }
> ```
>
> 效果如下图所示![](/assets/report_02.png)

* #### ctrl代码实现



