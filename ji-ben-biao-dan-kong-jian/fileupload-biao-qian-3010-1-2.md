# file_upload**单文件标签**

#### file_upload**单文件上传标签的属性 :**

> file_upload标签有4个属性分别为为id、name、size、label
>
> > ** *id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",input标签的默认size为5
> >
> > **label ：** label为标签的前缀标签属性,如label="name,true,2"；其中label属性中含有三个值，第一个值
> >
> > 为前缀标签的名字；第二个值为前缀标签是否加红色星号\*即必填项标志；第三个值为前缀标签的尺寸,
> >
> > 可填的数值范围为（1-12）,默认尺寸为1；引入方式：label="name,true,2" ； label="name,true" ；
> >
> > label="name" ；label="name,,2" 即三个值都非必填项
> >

#### file_upload标签的引入方式 :

```
    <@file_upload label="待上传文件,,2" id="myfile" name="myfile" size="8"/>

   
```

#### file_upload标签的显示结果:

![](/assets/file_upload.png)
