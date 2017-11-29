# modal\_iframe**标签**

#### 注：可参考角色管理、部门管理等功能模块。

#### modal\_iframe**标签的属性 :**

> modal\_iframe标签有4个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **modal\_title ：** 标题
> >
> > **drag：** 是否可拖动，默认不可拖动
> >
> > **class：** 样式\(不填：中等模态框;modal-lg：大模态框;modal-sm：小模态框\)
> >
> > **report\_window**【1.2】：true/flase，默认为false，用于区别报表窗口（ireport）和普通页面。
>>
> > **is_full_screen:** 为打开时是否全屏的属性，默认“false”,可填值"true","false"



#### modal\_iframe标签的引入方式 :

```
  主页面：
  <button type="button" class="btn btn-primary btn-lg" data-toggle="modal" data-target="#my_modal_lg_edit" onclick="test()">
    编辑(iframe)
  </button>

  <@modal_iframe id="my_modal_lg_edit" modal_title="编辑操作员" class="modal-lg" drag="true" />

  <script>
    function test() {
      $("#my_modal_lg_edit_iframe").attr("src","${base}/login/userLogin");
      $("#my_modal_lg_edit").modal("show");
    }
  </script>

  模态框中页面通过src请求后台跳转过去
```

#### modal\_iframe标签显示效果图 :

![](/assets/modal_iframe.png)

