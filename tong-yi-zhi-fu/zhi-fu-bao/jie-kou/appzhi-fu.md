# 接口方法

```
/**
App支付
@paramjson
*  body 商品描述
*  out_trade_no 订单号
*  tr_amt金额(单位分)
*  enable_pay_channels 可用渠道---可空，
与disable_pay_channels互斥，
比如可用花呗、余额宝，，则传入pcredit,moneyFund
*  disable_pay_channels禁用渠道---可空，
与enable_pay_channels互斥，
比如禁用花呗、信用卡，，则传入pcredit,creditCard
@return orderinfo
@throwsException
*/
publicstaticJSONObject sendPrepay(JSONObject json)throwsException;
```

# **调用示例：**

```
JSONObject json =newJSONObject();
json.put("body","充值");
json.put("out_trade_no","123");
json.put("tr_amt","1");
json.put("disable_pay_channels", "pcredit,creditCard");
JSONObject ret = AlipayService.sendPrepay(json);
System.out.println(ret);
```



