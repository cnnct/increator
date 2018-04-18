### 整合工作流云平台步骤：

##### 1、查看文档

登录[http://soeasycn.com/api](http://soeasycn.com/api)（此平台账号需要申请），打开：我的文档&gt;文档列表，找到“创建工作流云平台接口文档”，点击“查看”，即可查看工作流云平台接口的相关信息。包括工作流云平台提供的接口（Rxxx），以及想要接入工作流云平台的系统（业务平台）需要提供的接口（B）。

##### 2、签名规则

调用工作流云平台提供的接口，数据都使用JSON格式，使用的是公司大部分系统都在用的签名规则。

比如原本请求的JSON格式数据为：

```
{
 "trcode:":"login",
 "username":"aaa@qq.com"
}
```

现在要对以上各节点内容进行加密，加密的内容顺序有客户端自己定，假设对节点  
“trcode”和“usename”进行先后顺序加密，因此我们就可以把“trcode”和“usename”相加作为本次加密的key（描述了本次加密的先后顺序，内容用英文逗号分隔）和待加密的内容content（内容直接相连，中间不用任何符号分隔），再加上密钥（密钥在调用接口前需要配置到终端程序的缓存中）作为待加密的内容，测试密钥为“123456”，正式密钥系统上线前分配。  
以下以“123456”为例：

加密的key：trcode, usename

加密的内容为content：loginaaaa@qq.com123456

对content字符串数据进行MD5加密然后取32位大写值，

32位MD5大写：9FC5D689D6D9161D48F310A72D722737

再对以上32位MD5的大写值做SHA1加密，

40位SHA1大写：08C0C6B1F15477019CDD4C9FE94581089B1CDBCA

最后将40位SHA1大写值作为sign加入到原先的JSON数据中，同时也要带上key描述了节点加密的先后顺序，最后待提交到后台的JSON数据为：

```
{
 "trcode": "login", 
 "usename": "aaaa@qq.com", 
 "sign": "08C0C6B1F15477019CDD4C9FE94581089B1CDBCA"
}
```

参数带JSONArray子参数时，同时对里面的JSONArray类型数据也要循环按照JSONObject的签名规则进行加密，在对JSONObject内容进行加密时要排除掉里面的JSONArray类型数据，比如：

```
{
 "trcode": "login", 
 "usename": "aaaa@qq.com",
    "list": [
        {
            "id": "0", 
            "name": "消费"
        }, 
        {
            "id": "1", 
            "name": "充值"
        }
    ]
}
```

现在我们除了要对trcode和usename节点进行加密，添加key和sign外，同时对里面的JSONArray类型数据也要循环按照JSONObject的签名规则进行加密，在对JSONObject内容进行加密时要排除掉里面的JSONArray类型数据，比如这里最外层的key只对trcode和usename内容进行签名加密，而list子对象JSONObject中的key也只对本JSONObject的id和name内容进行加密，list子对象JSONObject相互之间加密互不干扰。

最后提交到后台的数据格式应该如下所示：

```
{
 "trcode": "login", 
 "usename": "aaaa@qq.com", 
 "sign": "B7C2D906C830F33AEFFCDBD2274044AC855FA14B",
    "list": [
        {
            "id": "0", 
            "name": "消费", 
            "sign": "6D9515CB3F253A928B02840F7033B0B355021D41"
        }, 
        {
            "id": "1", 
            "name": "充值", 
            "sign": "285FC4B68C9E2805C69FE6A927EAB360AEC8AF52"
        }
    ]
}
```

##### 3、基于新框架的平台调用工作流云平台示例

```
/** 
* 启动流程接口R001
*/
JSONObject caller = new JSONObject();
//公共参数
caller.put("trcode", "R001");
caller.put("sign", "xxx");
caller.put("syscode", "union");
caller.put("key", "xxx");
//R001接口特定参数
caller.put("user_id", "lucg");
caller.put("process_key", "TRIP-SkillOrdLiwf");
caller.put("business_key", "1");
JSONArray variables = new JSONArray();
JSONObject obj = new JSONObject();
obj.put("branch_id","10011009");
variables.add(obj);
caller.put("variables", variables);
//设置地址
FastJsonClient.setJSONSERVERURL("http://soeasycn.com/icwf/interf/workflow/R/R001");
//调用接口并返回参数
String returnStr = Tools.processNull(FastJsonClient.doPost(caller));
```



