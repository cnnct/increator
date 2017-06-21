# modal\_body和modal\_foot**标签**

#### modal\_body**标签的属性 :（**modal\_foot标签无属性**）**

> modal\_body标签有4个属性
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

#### modal\_body和modal\_foot标签的引入方式 :

```
  <button type="button" class="btn btn-primary btn-lg" data-toggle="modal" data-target="#my_modal">
           编辑
  </button>

  <@modal_body id="my_modal" modal_title="在线编辑" drag="true">
    内容
  </@modal_body>
  <@modal_foot>
    操作按钮
  </@modal_foot>
```

#### modal\_body和modal\_foot标签显示效果图 :



