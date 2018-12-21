# file\_upload**单文件上传标签**

#### file\_upload**单文件上传标签的属性 :**

#### 注1：使用文件上传（哪怕是普通的input type="file"）时，form表单最好加上enctype="multipart/form-data"属性，否则可能出现不选择文件提交到后台报错的问题。

#### 注2：后台接收含有此控件的表单提交时，controller方法的@RequestMapping中加上produces = "text/html; charset=UTF-8"，且该方法的返回值必须为String类型，否则会出现IE8和IE9下提交表单弹出下载提示的问题。示例如下：

```
    @RequestMapping(value="/save/{mark}", produces = "text/html; charset=UTF-8")
    @ResponseBody
    public String saveMerchantInfo(HttpServletRequest request, BsCardMerchantCust merchant, @PathVariable("mark") String mark,
            @RequestParam(value="file1",required=false) MultipartFile file1, @RequestParam(value="file2",required=false) MultipartFile file2) {
        ResultData resultData = new ResultData(Result_Code.SUCCESS);
        //获取当前操作员信息
        SysOperatorCust oper = getOper();
        //执行保存
        merchantServ.saveMerchantInfo(request, merchant, mark, oper, file1, file2);
        return resultData.toString();
    }
```

> file\_upload标签有4个属性分别为为id、name、size、label
>
> > ** \*id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为5
> >
> > **label ：** label为标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> > label="name" ；label="name,,2" 即三个值都非必填项，【2.5】版本后在view_para文件里的must_star_position属性可以控制must_star的加载左右位置，默认left


#### file\_upload标签的引入方式 :

```
    <@file_upload label="待上传文件,,2" id="myfile" name="myfile" size="8"/>
```

#### file\_upload标签的显示结果:

![](/assets/file_upload.png)

