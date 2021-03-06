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
> > 当前表：ACT_APRV_TRIP   历史表：ACT_APRV_TRI_HIS
> >     当前表记录当前审批表单最新状态及数据，进行审批或修改表单后，旧数据记录到历史表。
> > ```
>
> ##### 关于审批拒绝说明：
>
> > 审批拒绝的实现：审批拒绝回退，目前没有很好的实现方案，如果使用流程图的流转线来实现的话，流程图会非常乱，因此目前拒绝就是重新打回重新提交表单。后面再研究是否有更好的实现方案。

### 整合步骤：

##### 1、查看文档

登录[http://soeasycn.com/api](http://soeasycn.com/api)（此平台账号需要申请），打开：我的文档&gt;文档列表，找到“创建工作流云平台接口文档”，点击“查看”，即可查看工作流云平台接口的相关信息。包括工作流云平台提供的接口（Rxxx），以及想要接入工作流云平台的系统（业务平台）需要提供的接口（B）。

！！！！重点需要查看【概述/流程图绘制规范】

##### 2、基于新框架的业务平台调用工作流云平台示例，可配合框架demo进行学习开发

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

##### 



