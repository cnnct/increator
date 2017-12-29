# http接口服务使用配置

* ### 配置server接口类型

  > #### 1.当需要新建一类接口服务时，需要首先配置一个拦截器：
  >
  > #### ![](/assets/httplangjieqipeizhi.png) 2.在拦截器中初始化业务需要的数据：
  >
  > #### ![](/assets/interceptor.png) 3.在ServerAspet类中配置异常时要处理的业务：
  >
  > ![](/assets/serverAspet.png)  
  > ![](/assets/httpyichangchuli.png)
  >
  > #### 4.在InterFinallyServImpl类中配置finally要处理的业务：
  >
  > ![](/assets/httpfinallydo.png)
  >
  > #### 5.实际业务处理：
  >
  > ![](/assets/httpversion4.png)  
  > **注意** :接口上需要指定版本号，当请求固定版本号时url中需要加入版本，当请求的url中没有指定版本号，  
  > 则默认请求最新版本的接口,当请求的接口版本号不存在，则向下请求最新的接口，如有接口版本v1.1.1，v1.1.2，v1.1.5，现在请求v1.1.4接口，则执行的接口版本为v1.1.2，现在支持的最大接口版本为v999.9.9,注意小数点后面的数值最大为9
  >
  > #### 6.测试接口:
  >
  > #### ![](/assets/httpversion3.png)
  >
  > #### 7、跨域访问，特殊处理
  >
  > ##### com.cnnct.interf.interceptor.FrontEndInterceptor.preHandle方法中，在处理入参前增加header配置，如下：![](/assets/access.png)
  >
  > ##### 前端调用代码示例：
  >
  > ```
  > function loginx(){
  >         //入参
  >         var caller=new Object();
  >         caller.trcode="N001";
  >         caller.sign="123";
  >         caller.channel="10";
  >         caller.key="11111";
  >         
  >         caller.verifyMode="0";
  >         caller.verifyNo="13067816796";
  >         caller.handleType="20";
  >         caller.token="123";
  >         caller.login_name="admin";
  >         caller.ses_id="admin";
  >
  >         $j.ajax({
  >             crossDomain:true,//此参数必须
  >             url: 'http://localhost:8080/manageplat/interf/frontEnd/N002', //访问路径
  >             data: JSON.stringify(caller), //需要验证的参数，此处只能是字符串类型，不能是json对象类型
  >             type: 'POST', //传值的方式，只用POST，因为GET对入参长度有限制
  >             dataType :'json',
  >             contentType :"text/plain",//已测试，只能用此类型application/json请求时报错
  >             error: function() {//访问失败时调用的函数
  >                 alert("服务器错误！");
  >             },
  >             success: function(result) {
  >                 alert(JSON.stringify(result));                
  >             }
  >         });
  >        }
  > ```



