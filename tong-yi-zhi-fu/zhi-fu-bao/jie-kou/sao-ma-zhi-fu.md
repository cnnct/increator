/\*\*

扫码支付

**@param**json

\*  body 商品描述

\*  out\_trade\_no 订单号

\*  tr\_amt金额\(单位分\)

**@return**code\_url二维码链接

\*/

**publicstatic**JSONObject sendWebPrepay\(JSONObject json\)**throws**Exception;

# **调用示例：**

JSONObject json =**new**JSONObject\(\);

json.put\("body","充值"\);

json.put\("out\_trade\_no ","123"\);

json.put\("tr\_amt","1"\);

JSONObject ret = AlipayService.sendWebPrepay\(json\);

System.out.println\(ret\);

 

