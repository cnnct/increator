# modal\_iframe**标签**

#### modal\_iframe**标签的属性 :**

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
    <form action="">
      <div class="row top_margin_20">
        <div class="col-xs-3">
          <label for="">用户姓名<span class="must_star">*</span></label>
          <input type="text" id="" class="form-control" placeholder="请输入姓名"></input>
        </div>
        <div class="col-xs-3">
          <label for="">手机号码<span class="must_star">*</span></label>
          <input type="text" id="" class="form-control" placeholder="请输入手机号码"></input>
        </div>
        <div class="col-xs-3">
          <label for="name">证件卡号<span class="must_star">*</span></label>
          <input type="text" id="name" class="form-control" placeholder="请输入证件卡号"></input>
        </div>
        <div class="col-xs-3">
          <label for="">市民卡号<span class="must_star">*</span></label>
          <input type="text" id="" class="form-control" placeholder="请输入市民卡号"></input>
        </div>
      </div>
      <div class="row top_margin_20">
        <div class="col-xs-3">
          <label for="">证件类型<span class="must_star">*</span></label>
          <select name="" class="form-control">
            <option value="">全部</option>
            <option value="">身份证</option>
          </select>
        </div>
      </div>
      <div class="row top_margin_20">
        <div class="col-xs-4">
          <label for="">实名<span class="must_star">*</span></label>
          <select name="" class="form-control">
            <option value="">全部</option>
          </select>
        </div>
        <div class="col-xs-4">
          <label for="">绑卡<span class="must_star">*</span></label>
          <select name="" class="form-control">
            <option value="">全部</option>
          </select>
        </div>
      </div>
    </form>
  </@modal_body>
  <@modal_foot>
    <a type="submit" class="btn btn-primary" data-dismiss="modal">提交更改</a>
  </@modal_foot>
```

#### modal\_body和modal\_foot标签显示效果图 :



