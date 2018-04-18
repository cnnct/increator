### 整合须知：

> ##### 业务平台和工作流云平台整合原则是松耦合原则，这是经过多种尝试之后选择的，具体体现在以下几个方面：
>
> > ①业务数据：业务数据由业务系统存储处理，需在业务端的表中增加字段，保存工作流云平台返回的流程实例id;
> >
> > ②业务表单：业务平台的表单由业务平台自行开发（工作流云平台的表单功能有限，不适合复杂业务）；
>
> ##### 数据库设计方案：
>
> > ①采用主表、子表的方式设计，这样扩展性更好。
> >
> > 审批总表act\_aprv，主要字段：流水号、用户id、发起时间、状态（0未审批2审批中3已审批4已拒绝）、审批类型（！！！很关键，主要用来和子表进行关联，类型值就是子表的表名的后缀！！！）
> >
> > ```
> > 审批总表ACT_APRV，主要字段：
> >     流水号(主键)、
> >     用户id、
> >     发起时间、
> >     状态（0未审批2审批中3已审批4已拒绝）、
> >     审批类型（！！！很关键，主要用来和子表进行关联，类型值就是子表的表名的后缀，如TRIP表示差旅审批！！！）
> >     流程实例ID
> >
> > 审批子表ACT_APRV_TRIP，根据业务系统自身的审批类型拆分成多张表，每种类型的业务字段根据实际情况增减。
> > ```
> >
> > ②采用当前表、历史表的设计模式
> >
> > ```
> > ACT_APRV_TRIP ACT_APRV_TRI_HIS
> > 当前表记录当前审批表单最新状态及数据，进行审批或修改表单后，旧数据记录到历史表。
> > ```
>
> ##### 关于审批拒绝说明：
>
> > 审批拒绝的实现：

### 整合步骤：

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

##### 3、基于新框架的业务平台调用工作流云平台示例

```
/** 
* 启动流程接口R001
*/
JSONObject caller = new JSONObject();
//公共参数
caller.put("trcode", "R001");
caller.put("sign", "xxx");
//系统编号，此编号为业务平台与工作流云平台共同设定
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

##### 4、业务平台建表规范方案

&gt;

