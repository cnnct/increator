# file\_mult\_upload**标签**

#### file\_mult\_upload**标签的属性 :**

#### 注1：此标签在modal\_body,modal\_foot中存在问题,可以使用modal\_iframe代替。

> file\_mult\_upload标签属性如下：
>
> **其中必填项加上了\*号，如下所示 :**
>
> > \***id ：** id属性
> >
> > \***name ：** name属性
> >
> > \***url：** 请求的url
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",file\_mult\_upload标签的默认size为12
> >
> > **wrap\_have ：** 是否同时上传缩略图，可以填写的值为“false”和“true”
> >
> > **file\_num\_limit ：**上传文件数量限制
> >
> > **orig\_upload\_batch**【2.2】**：**之前上传的文件批次号--用于编辑时，即附件表中的文件批次号
> >
> > **use\_opt**【2.2】**：**是否启用操作按钮--页面上的旋转和删除，注：如果值为true，则后台上传方法必须使用新版，即返回Map&lt;String, Object&gt;的那两个上传方法，同时业务controller中必须返回上传文件返回页面的ResultData中必须put进去fileId，此fileId从上传方法返回的Map&lt;String, Object&gt;中取出，示例请看TagDemoCtrl中的代码。

#### file\_mult\_upload标签的引入方式 :

```
<@file_mult_upload id="test_upload2" name="test_upload_name2" size="3" url="${base}/tag/uploadMultFile" />
```

#### file\_mult\_upload标签显示效果图 :

![](/assets/file_mult_upload.png)

#### 后台接收上传的文件时注意事项 :

1、不管是普通的上传文件，还是file\_mult\_upload标签上传文件，方法返回值必须为String  
，于此同时，@RequestMapping中加入produces = "text/html; charset=UTF-8"。如下所示：

```
@RequestMapping(value="/uploadMultFile", produces = "text/html; charset=UTF-8")
```

2、不管是普通的上传文件，还是file\_mult\_upload标签上传文件，推荐使用后台controller参数中加如下参数获取文件的方式：

```
@RequestParam("test_upload_name2") MultipartFile[] files
```

其中“test\_upload\_name2"为页面input或者file\_mult\_upload标签的name属性。

3、\(1\)使用普通input上传文件时，需要随机生成一个唯一标识，可用UUID，如下即可：

```
String uuid = UUID.randomUUID().toString();//文件唯一标识
```

\(2\)使用file\_mult\_upload标签时，后台需要获取uuid参数，由于springmvc特性，如下即可：

```
public Object uploadMultFile (@RequestParam("test_upload_name2") MultipartFile[] files, String uuid) {
    ......
}
```

4、此uuid为同一批file\_mult\_upload标签上传的文件唯一标识\(包括继续添加后的上传\)，默认将uuid作为在FTP上创建的存放同一批上传文件的文件夹名，也可以将此uuid存入数据库作为同一批文件的标识。

然后通过BaseCtrl中的公共上传文件方法上传，详细可见com.cnnct.module.demo.TagDemoCtrl中的uploadMultFile方法。

然后包含多文件上传标签的表单提交后，后台获取上传文件批次号的代码如下：

```
@RequestParam("demo_val") String demo

// 上传文件批次号
String uploadBatch = null;
if (demo!= null && !"".equals(demo)) {
    JSONObject obj = JSONObject.parseObject(demo);
    // 这个对应sys_attachment表中UPLOAD_BATCH字段的值,可以用这个查出文件信息
    uploadBatch = obj.getString("fileKey");
}
```



