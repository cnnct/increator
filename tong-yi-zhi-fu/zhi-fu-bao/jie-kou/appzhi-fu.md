/\*\*

App支付

**@param**json

\*  body 商品描述

\*  out\_trade\_no 订单号

\*  tr\_amt金额\(单位分\)

\*  enable\_pay\_channels 可用渠道---可空，

与disable\_pay\_channels互斥，

比如可用花呗、余额宝，，则传入pcredit,moneyFund

\*  disable\_pay\_channels禁用渠道---可空，

与enable\_pay\_channels互斥，

比如禁用花呗、信用卡，，则传入pcredit,creditCard

**@return orderinfo**

**@throws**Exception

\*/

**publicstatic**JSONObject sendPrepay\(JSONObject json\)**throws**Exception;

# **调用示例：**

JSONObject json =**new**JSONObject\(\);

json.put\("body","充值"\);

json.put\("out\_trade\_no","123"\);

json.put\("tr\_amt","1"\);

json.put\("disable\_pay\_channels", "pcredit,creditCard"\);

JSONObject ret = AlipayService.sendPrepay\(json\);

System.out.println\(ret\);



