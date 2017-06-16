# 模态弹框

#### alert弹出框引入方式：

```
    alert("Are you sure?");

    alert({ 
        title: "Destroy planet?",
        message: "Are you sure?", 
    });
```

![](/assets/alert1.png)

![](/assets/alert2.png)

#### confirm弹出框引入方式：

```
           confirm({ 
                title: "Destroy planet?",
                message: "Are you sure?", 
                callback: function(result){ //回调函数
                        if(result){
                            alert("true");
                        }
                }
           })
```

![](/assets/confirm.png)

#### prompt弹出框引入方式：



