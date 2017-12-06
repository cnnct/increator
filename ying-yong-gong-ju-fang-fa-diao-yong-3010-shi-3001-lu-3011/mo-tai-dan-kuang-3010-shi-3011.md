# 模态弹框

#### alert弹出框引入方式：

```
            alert("Are you sure?");

            alert({ 
                title: "Destroy planet?",
                message: "Are you sure?", 
                okBtnName:"确认",
            });
            
            【1.4】alert({ 
                title: "Destroy planet?",
                message: "Are you sure?", 
                okBtnName:"确认",
                callback：function(){console.log("ok")}
            });

```
【1.4】版本后alert支持加入回调函数
#### alert弹出框显示结果：

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
                },
                okBtnName:"确认",
                cancelBtnName:"取消",
           })
```

#### confirm弹出框显示结果：

![](/assets/alert3.png)

#### prompt弹出框引入方式：

```
           prompt({ 
                 title: "What is your name?", 
                 callback: function(result){ 
                       if(result){
                             alert("true");
                      }
                 },
                  okBtnName:"确认",
                  cancelBtnName:"取消",
             })
```

#### prompt弹出框显示结果：

![](/assets/alert4.png)

#### load加载弹出框引入方式：

```
            load();

            load('close');//关闭加载弹出框
```

#### load加载弹出框显示结果：

![](/assets/load.png)

