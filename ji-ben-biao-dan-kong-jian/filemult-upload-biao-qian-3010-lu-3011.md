# file\_mult\_upload**标签**

#### file\_mult\_upload**标签的属性 :**

> file\_mult\_upload标签有4个属性
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

#### file\_mult\_upload标签的引入方式 :

```
<@file_mult_upload id="test_upload2" name="test_upload_name2" size="3" url="/tag/uploadMultFile" />
```

#### file\_mult\_upload标签显示效果图 :

![](/assets/file_mult_upload.png)

#### 后台接收上传的文件时注意事项 :

1、不管是普通的上传文件，还是file\_mult\_upload标签上传文件，后台controller参数中都需要加：

```
@RequestParam("test_upload_name2") MultipartFile[] files
```

其中“test\_upload\_name2"为页面input或者file\_mult\_upload标签的name属性。

2、\(1\)使用普通input上传文件时，需要随机生成一个唯一标识，可用UUID，如下即可：

```
String uuid = UUID.randomUUID().toString();//文件唯一标识
```

\(2\)使用file\_mult\_upload标签时，后台需要获取uuid参数，由于springmvc特性，如下即可：

```
public Object uploadMultFile (@RequestParam("test_upload_name2") MultipartFile[] files, String uuid) {
    ......
}
```

3、此uuid为同一批file\_mult\_upload标签上传的文件唯一标识\(包括继续添加后的上传\)，默认将uuid作为在FTP上创建的存放同一批上传文件的文件夹名，也可以将此uuid存入数据库作为同一批文件的标识。

然后通过如下代码遍历获取文件并上传：

```
List<String> list = uploadFile(files, uuid);//上传的文件全路径名集合
```



