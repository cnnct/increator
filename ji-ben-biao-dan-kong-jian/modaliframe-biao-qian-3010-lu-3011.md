# modal\_iframe**标签**

#### 注：已过时，推荐使用modal标签。可参考角色管理、部门管理等功能模块。

#### modal\_iframe**标签的属性 :**

> modal\_iframe标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id：**id属性
> >
> > **modal\_title：**标题
> >
> > **drag：**是否可拖动，默认不可拖动
> >
> > **class：**样式\(不填：中等模态框;modal-lg：大模态框;modal-sm：小模态框\)
> >
> > **report\_window**【1.2】**：**true/flase，默认为false，用于区别报表窗口（ireport）和普通页面。
> >
> > **is\_full\_screen：**为打开时是否全屏的属性，默认“false”,可填值"true","false"
> >
> > **foot\_content\_position【2.3】：**模态框脚中内容的位置\(默认right\)：left\(左\)、right\(右\)、center\(居中\)，如果为center，那么模态框脚中标签的一些属性可能会失效，比如button的size、position。

#### modal\_iframe标签的引入方式 :

```
  主页面：
  设置一个onclick="test()"事件,比如按钮：

  引入modal_iframe：
  <@modal_iframe id="modal_edit" modal_title="编辑角色" class="modal-lg"/>

  写一个onclick触发的方法：
  <script>
    function test() {
      通过modal_iframe的id获取此对象再调用modalShow(url)方法,此url为后台controller中方法的url：
      $("#modal_edit").modalShow("/sys/auth/role/edit/" + id);
      注意：【2.0】版本后modalShow方法有所调整，需要加入项目名，如下： $("#modal_edit").modalShow("${base}/sys/auth/role/edit/" + id);

    }
  </script>
```

#### modal\_iframe标签显示效果图 :

![](/assets/modal_iframe.png)

