# 模态弹框

#### alert弹出框引入方式：

```
            alert("Are you sure?");

            alert({ 
                title: "Destroy planet?",
                message: "Are you sure?", 
                okBtnName:"确认",
            });
```

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
                }
           })
```

#### confirm弹出框显示结果：

![](/assets/confirm.png)

#### prompt弹出框引入方式：

```
           prompt({ 
                 title: "What is your name?", 
                 callback: function(result){ 
                       if(result){
                             alert("true");
                      }
                 }
             })
```

#### prompt弹出框显示结果：

![](/assets/prompt.png)

#### load加载弹出框引入方式：

```
            load();

            load('close');//关闭加载弹出框
```

#### load加载弹出框显示结果：

![](/assets/load.png)

