# modal\_iframe**标签**

#### modal\_iframe**标签的属性 :**

> modal\_iframe标签有4个属性
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > **modal\_title ：** 标题
> >
> > \***drag：** 是否可拖动，默认不可拖动
> >
> > \***class：** 样式\(不填：中等模态框;modal-lg：大模态框;modal-sm：小模态框\)

#### modal\_iframe标签的引入方式 :

```
  <button type="button" class="btn btn-primary btn-lg" data-toggle="modal" data-target="#my_modal_lg_edit" onclick="test()">
    编辑(iframe)
  </button>

  <@modal_iframe id="my_modal_lg_edit" modal_title="编辑操作员" class="modal-lg" drag="true" />

  <script>
    function test() {
      $("#my_modal_lg_edit_iframe").attr("src","${base}/login/userLogin");
    }
  </script>
```

#### modal\_iframe标签显示效果图 :



