/\*\*

web支付

**@param**json

\*  body 商品描述

\*  out\_trade\_no 订单号

\*  tr\_amt金额\(单位分\)

\*  enable\_paymethod 可用渠道---可空，与disable\_paymethod互斥，

比如可用余额、网银、借记卡快捷，，则传入directPay^bankPay^debitCardExpress

\*  disable\_paymethod禁用渠道---可空，与enable\_paymethod互斥，

比如禁用信用卡快捷，，则传入creditCardExpress

**@return**code\_url web支付form

\*/

**publicstatic**JSONObject sendWebPay\(JSONObject json\)**throws**Exception;

# **调用示例：**

JSONObject json =**new**JSONObject\(\);

json.put\("body","充值"\);

json.put\("out\_trade\_no ","123"\);

json.put\("tr\_amt","1"\);

json.put\("enable\_paymethod", "directPay^bankPay^debitCardExpress^cash"\);

JSONObject ret = AlipayService.sendWebPay\(json\);

System.out.println\(ret\);



